<template>
    <div class="container">
        <img src="/img/morcego.png" alt="Your mob apperence" v-show="show_img1">
        <img src="/img/tartaruga.png" alt="Your mob apperence" v-show="show_img2">
        <img src="/img/urso.png" alt="Your mob apperence" v-show="show_img3">
        
        <button class="btn-pick" @click="pickMob" title="click to pick your mob appearance">Pick</button>
        
        <div class="wrapper-buttons">
            <button @click="slideMobs('previous')">Previous</button>
            <button @click="slideMobs('next')">Next</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'mobChoose',
    data() {
        return {
            show_img1: true,
            show_img2: false,
            show_img3: false,
            n: 0
        }
    },
    methods: {
        async pickMob() {
            
            //Get button, add class or remove to style when clicked
            const btn = document.querySelector('.btn-pick');
            btn.classList.toggle('clicked')

            //Set interval
            setTimeout(() => {
                btn.style.pointerEvents = 'none';
                btn.style.opacity = "80%"
            }, 0)
            setTimeout(() => {
                btn.style.pointerEvents = 'initial';
                btn.style.opacity = "100%"
            }, 1200)


            //Get user
            const loggedDB = await fetch('http://localhost:3000/logado');
            const user = await loggedDB.json();
            //Get mob
            const mobsDB = await fetch('http://localhost:3000/mobs');
            const mobs = await mobsDB.json();

            for (var i in mobs) {
                if (user[0].name == mobs[i].owner && user[0].passwd == mobs[i].owner_passwd) {
                    const idMob = mobs[i].id

                    //Put appearance in mob database
                    const data = JSON.stringify({mob_appearance: this.n})
                    const updateMob = await fetch(`http://localhost:3000/mobs/${idMob}`, {
                        method: 'PATCH',
                        headers: {"Content-Type" : "application/json"},
                        body: data
                    });
                    const res = await updateMob.json();
                    console.log(res)
                }
            }
            
            

        },

        slideMobs(direction) {
            const btn = document.querySelector('.btn-pick');
            btn.classList.remove('clicked')
    
            if (direction == 'next') {
                this.n++
                if (this.n == 3) {
                    this.n = 0
                }
            }else if (direction == 'previous') {
                this.n--
                if (this.n == -1) {
                    this.n = 2
                }
            }

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
                    console.log("SEU MOB É " + mobs[i].mob_appearance)
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
    mounted() {
        this.mob_appearance()
    }
}
</script>

<style scoped>

    .container {
        border: 2px solid var(--color-black-default);
        padding: 0;
        margin: 0;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 10fr 1fr 1fr;
        width: 30%;
        height: 100%;
    
    }

    .container img {
        width: 100%;
        height: 100%;
    }

    .container .btn-pick {
        width: 100%;
        height: 100%;
        font: 1rem var(--font-primary);
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
    }

    .container .wrapper-button-pick .btn-pick.clicked {
        background: var(--color-secondary-shadow);
    }

    .container .wrapper-buttons button {
        width: 50%;
        height: 100%;
        border: 2px solid var(--color-black-default);
        font: 1rem var(--font-primary);
        background-color: var(--color-secondary);
    }

</style>