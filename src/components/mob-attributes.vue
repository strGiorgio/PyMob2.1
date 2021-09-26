<template>
    <div class="wrapper-attr">
        <div>
            <label>Level:</label> 
            <label>Points:</label>
        </div>
        
        <div>
            <label>HP:</label> 
            <span>BUY</span>
        </div>
        <div>
            <label>Defense:</label> 
            <span>BUY</span>
        </div>
        <div>
            <label>strenght:</label> 
            <span>BUY</span>
        </div>
        <div>
            <label>Stamina:</label> 
            <span>BUY</span>
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

    .wrapper-attr button {
        width: 40%;
        padding: 30px 20px;
        background-color: var(--color-green-secondary);
        border: 2px solid var(--color-black-default);
        align-self: end;
    }

</style>