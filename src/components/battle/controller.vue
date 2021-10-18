<template>
    <div class="controller">
        <div class="wrapper-img">
            <img src="/img/morcego-avatar.png" alt="" v-show="show_img1">
            <img src="/img/tartaruga-avatar.png" alt="" v-show="show_img2">
            <img src="/img/urso-avatar.png" alt="" v-show="show_img3">
        </div>
        <div class="controller-buttons">
            <progress id="progress-bar" :max="max_hp" value="20"></progress>
            <span>HP: {{ current_hp }} / {{ max_hp }}</span>
            <button>Atack</button>
            <button>Atack Especial</button>
            <button>Escape</button>
            <button>Regenerate</button>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'controller',
    data() {
        return {
            max_hp: null,
            current_hp: null,
            show_img1: false,
            show_img2: true,
            show_img3: false
        }
    },
    methods: {
        async getInfos() {
            //get user logged
            const loggedDB = await fetch('http://localhost:3000/logado');
            const user = await loggedDB.json()
            //get mob
            const mobsDB = await fetch('http://localhost:3000/mobs');
            const mobs = await mobsDB.json()

            for (var i in mobs) {
                if (user[0].name == mobs[i].owner && user[0].passwd == mobs[i].owner_passwd){
                    this.max_hp = mobs[i].hp
                    this.current_hp = mobs[i].current_hp
                }
            }

        },

        async mob_appearance() {
            //GET USER LOGGED
            const userLogged = await fetch('http://localhost:3000/logado');
            const user = await userLogged.json()
            //GET MOBs
            const mobsDatabase = await fetch('http://localhost:3000/mobs');
            const mobs = await mobsDatabase.json()

            for (var i in mobs) {
                if (user[0].name == mobs[i].owner && user[0].passwd == mobs[i].owner_passwd) {
                    var value = mobs[i].mob_appearance
                    this.n = value;
                    
                    switch (this.n) {
                    case 0:
                        this.show_img1 = true;
                        this.show_img2 = false;
                        this.show_img3 = false;
                        break
                    case 1:
                        this.show_img1 = false;
                        this.show_img2 = true;
                        this.show_img3 = false;
                        break
                    case 2:
                        this.show_img1 = false;
                        this.show_img2 = false;
                        this.show_img3 = true;
                        break
                    default:
                        break
                    }
                }
            }
        }
    },
    created() {
        this.getInfos();
        this.mob_appearance();
    }
}
</script>

<style scoped>
    .controller {
        width: 450px;
        height: 160px;
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        position: absolute;
        bottom: 10px; 
        right: 50px;
        transform: translateX(450px);
        animation: slideToLeft 2s forwards;
        padding: 5px;
        display: grid;
        grid-template-columns: 1.3fr 2fr;
        
    }

    .wrapper-img img{
        width: 90%;
        height: 100%;
        border: 1px solid var(--color-black-default);
    }

    .controller-buttons {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr fr;
        grid-gap: 5px;
    }
    
    .controller-buttons progress {
        width: 100%;
        border: 0px solid var(--color-black-default);
        grid-column: 1 / 3;
        position: relative;
    }

    .controller-buttons progress::-webkit-progress-bar {
        background-color: var(--color-white-default);
        height: 35px;
    }
    
    .controller-buttons progress::-moz-progress-bar {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons progress::-webkit-progress-value {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons progress::-moz-progress-value {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons span {
        font: 1.3rem var(--font-primary);
        position: absolute;
        right: 60px;
        top: 17px;
    }

    .controller-buttons button {
        background-color: var(--color-gray);
        border: 2px solid var(--color-black-default);
        font: 1rem var(--font-primary);
        transition: .5s;
    }

    .controller-buttons button:hover {
        opacity: 70%;
    }

    @keyframes slideToLeft {
        to {
            transform: translateX(0);
        }
    }
</style>