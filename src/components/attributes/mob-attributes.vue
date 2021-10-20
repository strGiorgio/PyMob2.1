<template>
    <div class="wrapper-attr">
        <p>{{ msg }}</p>
        <div>
            <label>Level: <span class="values">{{ level }}</span></label> 
            <label>Points: <span class="values">{{ points }}</span></label>
        </div>
        
        <div>
            <label>HP: <span class="values">{{ hp }}</span></label> 
            <span class="buttons" @click="marketplace('hp')">BUY</span>
        </div>
        <div>
            <label>Defense: <span class="values">{{ defense }}</span></label> 
            <span class="buttons" @click="marketplace('defense')">BUY</span>
        </div>
        <div>
            <label>strength: <span class="values">{{ strength }}</span></label> 
            <span class="buttons" @click="marketplace('strength')">BUY</span>
        </div>
        <div>
            <label>Stamina: <span class="values">{{ stamina }}</span></label> 
            <span class="buttons" @click="marketplace('stamina')">BUY</span>
        </div>

        <router-link class="router-button" @click="initBattle" to="/battle">Start Battle</router-link>
    </div>
</template>
<script>
export default {
    name: 'mobAttributes',
    data() {
        return {
            hp: null,
            defense: null,
            strength: null,
            stamina: null,
            level: null,
            points: null,
            msg: null
        }
    },
    methods: {
        async getMobAttributes() {
            const getUserLogged = await fetch('http://localhost:3000/logado')
            const dbLogged = await getUserLogged.json()
            console.log(dbLogged)

            const getMob = await fetch('http://localhost:3000/mobs');
            const dbMobs = await getMob.json()

            for (var i in dbMobs) {
                if (dbMobs[i].owner == dbLogged[0].name && dbMobs[i].owner_passwd == dbLogged[0].passwd) {
                    console.log('Certo!')
                    
                    this.hp = dbMobs[i].hp;
                    this.defense = dbMobs[i].defense;
                    this.strength = dbMobs[i].strength;
                    this.stamina = dbMobs[i].stamina;
                    this.level = dbMobs[i].level;
                    this.points = dbMobs[i].points;
                }
            }
        },

        async marketplace(attr) {
            //Getting user logged
            const getUserLogged = await fetch('http://localhost:3000/logado')
            const dbLogged = await getUserLogged.json();

            //Getting user mob
            const getMob = await fetch('http://localhost:3000/mobs');
            const dbMobs = await getMob.json();

            const message = document.querySelector('.wrapper-attr p');

            for (var i in dbMobs) {
                if (dbLogged[0].name == dbMobs[i].owner && dbLogged[0].passwd == dbMobs[i].owner_passwd) {
                    var value = null;
                    var pointsV = dbMobs[i].points
                    const id = dbMobs[i].id;

                    //Time interval to buy
                    const button1 = document.querySelectorAll('.buttons')[0];
                    const button2 = document.querySelectorAll('.buttons')[1];
                    const button3 = document.querySelectorAll('.buttons')[2];
                    const button4 = document.querySelectorAll('.buttons')[3];
                    setTimeout(() => {
                        button1.classList.add('inactive');
                        button2.classList.add('inactive');
                        button3.classList.add('inactive');
                        button4.classList.add('inactive');
                        }, 0)
                    setTimeout(() => {
                        button1.classList.remove('inactive');
                        button2.classList.remove('inactive');
                        button3.classList.remove('inactive');
                        button4.classList.remove('inactive');
                        }, 1000)

                    if (pointsV > 0) {
                        var dataAttr = JSON.stringify({attr : value});
                        switch (attr) {
                            case 'hp':
                                value = dbMobs[i].hp + 1
                                pointsV--
                                console.log('you bought', attr, value, pointsV)
                                dataAttr = JSON.stringify({hp : value});
                                this.hp++
                                this.points = pointsV
                                break
                            case 'defense':
                                value = dbMobs[i].defense + 1
                                pointsV--
                                console.log('you bought', attr, value, pointsV)
                                dataAttr = JSON.stringify({defense : value});
                                this.defense++
                                this.points = pointsV
                                break
                            case 'strength':
                                value = dbMobs[i].strength + 1
                                pointsV--
                                console.log('you bought', attr, value, pointsV)
                                dataAttr = JSON.stringify({strength : value});
                                this.strength++
                                this.points = pointsV
                                break
                            case 'stamina':
                                value = dbMobs[i].stamina + 1
                                pointsV--
                                console.log('you bought', attr, value, pointsV)
                                dataAttr = JSON.stringify({stamina : value});
                                this.stamina++
                                this.points = pointsV
                                break
                        }
                        message.style.color = 'var(--color-green-default)';
                        this.msg = `You bought ${attr}`;
                        setTimeout(() => {this.msg = null}, 1000)

                        //Put infos (attributes) in database
                        const updateMob = await fetch(`http://localhost:3000/mobs/${id}`, {
                            method: 'PATCH',
                            headers: {"Content-Type" : "application/json"},
                            body: dataAttr
                        });
                        const res = await updateMob.json();
                        console.log(res)

                        //Put infos (points) in databse
                        const dataPoints= JSON.stringify({points: pointsV})
    
                        const updatePoints = await fetch(`http://localhost:3000/mobs/${id}`, {
                            method: 'PATCH',
                            headers: {"Content-Type" : "application/json"},
                            body: dataPoints
                        });
                        const resPoints = await updatePoints.json();
                        console.log(resPoints)

                    } else {
                        console.log('Not enough money!')
                        message.style.color = 'var(--color-red-default)';
                        this.msg = "You don`t have enough money!";
                        setTimeout(() => {this.msg = null}, 1000)
                    }
                }
            }
        },

        async initBattle() {
            const getUserLogged = await fetch('http://localhost:3000/logado')
            const dbLogged = await getUserLogged.json();

            //Getting user mob
            const getMob = await fetch('http://localhost:3000/mobs');
            const dbMobs = await getMob.json();

            for (var i in dbMobs) {
                if (dbLogged[0].name == dbMobs[i].owner && dbLogged[0].passwd == dbMobs[i].owner_passwd) {
                    const current = dbMobs[i].hp;
                    const data = JSON.stringify({current_hp: current});
                    const id = dbMobs[i].id;

                    const updateDB = await fetch(`http://localhost:3000/mobs/${id}`, {
                        method: 'PATCH',
                        headers: {"Content-Type" : "application/json"},
                        body: data
                    });
                    const res = await updateDB.json()

                    console.log(res)
                }
            }
            document.location.reload(true)

        }

    },
    mounted() {
        this.getMobAttributes()
    }
}
</script>

<style scoped>
    .wrapper-attr {
        width: 70%;
        height: 100%;
        padding: 50px;
        font: 2rem var(--font-primary);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .wrapper-attr p {
        color: var(--color-green-secondary);
        font: 1.3rem var(--font-primary);
        text-align: center;
    }

    .wrapper-attr div {
        display: flex;
        justify-content: space-between;
    }

    .wrapper-attr div:nth-of-type(1) {
        justify-content: space-around;
    }

    .wrapper-attr .buttons {
        background-color: var(--color-green-secondary);
        padding: 5px;
        font-size: 1.4rem;
        border: 2px solid var(--color-black-default);
        cursor: pointer;
    }

    .wrapper-attr .buttons:hover {
        opacity: 70%;
    }

    .wrapper-attr .buttons.inactive {
        pointer-events: none;
        opacity: 70%;
    }

    .wrapper-attr .values {
        border: none;
        background: none;
        color: var(--color-green-secondary);
    }

    .wrapper-attr .router-button {
        width: 300px;
        padding: 30px 20px;
        background-color: var(--color-green-secondary);
        border: 2px solid var(--color-black-default);
        align-self: end;
        text-decoration: none;
        color: var(--color-black-default);
        text-align: center;
    }

</style>