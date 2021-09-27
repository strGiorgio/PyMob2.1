<template>
    <div class="wrapper-attr">
        <div>
            <label>Level: <span class="values">{{ level }}</span></label> 
            <label>Points: <span class="values">{{ points }}</span></label>
        </div>
        
        <div>
            <label>HP: <span class="values">{{ hp }}</span></label> 
            <span @click="marktplace('hp')">BUY</span>
        </div>
        <div>
            <label>Defense: <span class="values">{{ defense }}</span></label> 
            <span @click="marktplace('defense')">BUY</span>
        </div>
        <div>
            <label>strenght: <span class="values">{{ strenght }}</span></label> 
            <span @click="marktplace('strenght')">BUY</span>
        </div>
        <div>
            <label>Stamina: <span class="values">{{ stamina }}</span></label> 
            <span @click="marktplace('stamina')">BUY</span>
        </div>

        <button>Start battle</button>
    </div>
</template>
<script>
export default {
    name: 'mobAttributes',
    data() {
        return {
            hp: null,
            defense: null,
            strenght: null,
            stamina: null,
            level: null,
            points: null
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
                    this.strenght = dbMobs[i].strenght;
                    this.stamina = dbMobs[i].stamina;
                    this.level = dbMobs[i].level;
                    this.points = dbMobs[i].points;
                }
            }
        },

        async marktplace(attr) {
            //Getting user logged
            const getUserLogged = await fetch('http://localhost:3000/logado')
            const dbLogged = await getUserLogged.json();

            //Getting user mob
            const getMob = await fetch('http://localhost:3000/mobs');
            const dbMobs = await getMob.json();

            for (var i in dbMobs) {
                if (dbLogged[0].name == dbMobs[i].owner && dbLogged[0].passwd == dbMobs[i].owner_passwd) {
                    

                    var value = null;
                    var points = dbMobs[i].points

                    if (points > 0) {
                        switch (attr) {
                            case 'hp':
                                value = dbMobs[i].hp + 1
                                points--
                                console.log('you bought', attr, value, points)
                                break
                            case 'defense':
                                value = dbMobs[i].defense + 1
                                points--
                                console.log('you bought', attr, value, points)
                                break
                            case 'strenght':
                                value = dbMobs[i].strenght + 1
                                points--
                                console.log('you bought', attr, value, points)
                                break
                            case 'stamina':
                                value = dbMobs[i].stamina + 1
                                points--
                                console.log('you bought', attr, value, points)
                                break
                        } 
                    } else {
                        console.log('Not enough money!')
                    }

                    //const datajson = JSON.stringify({attr : })
                    //const updateMob = await fetch('http://localhost:3000/mobs', {
                    //    method: 'PATCH',
                    //    headers: {"Content-Type" : "application/json"},
                    //    body: datajson
                    //})

                    //const res = await updateMob.json();
                    //console.log(res)
                }
                
            }

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

    .wrapper-attr div {
        display: flex;
        justify-content: space-between;
    }

    .wrapper-attr div:nth-of-type(1) {
        justify-content: space-around;
    }

    .wrapper-attr span {
        background-color: var(--color-green-secondary);
        padding: 5px;
        font-size: 1.4rem;
        border: 2px solid var(--color-black-default);
        cursor: pointer;
    }

    .wrapper-attr span:hover {
        opacity: 70%;
    }

    .wrapper-attr .values {
        border: none;
        background: none;
        color: var(--color-green-secondary);
    }

    .wrapper-attr button {
        width: 40%;
        padding: 30px 20px;
        background-color: var(--color-green-secondary);
        border: 2px solid var(--color-black-default);
        align-self: end;
    }

</style>