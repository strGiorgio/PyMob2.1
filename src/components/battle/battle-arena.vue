<template>
    <div class="battle-arena">
        <div class="wrapper-floor-mobs">
            <img class="floor-arena" src="/img/arena.png" alt="Floor arena">

            <!-- Mobs -->
            <img class="mob-image" src="/img/morcego-idle.png" alt="Mob idle" v-show="show_img1">
            <img class="mob-image" src="/img/tartaruga-idle.png" alt="Mob idle" v-show="show_img2">
            <img class="mob-image" src="/img/urso-idle.png" alt="Mob idle" v-show="show_img3">

            <!-- Enemies -->
            <img class="enemy-image" src="/img/morcego.png" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'battleArena',
    data() {
        return {
            show_img1: false,
            show_img2: true,
            show_img3: false,
        }
    },
    methods: {
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
    created() {
        this.mob_appearance()
    }
}
</script>

<style scoped>
    .battle-arena {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .battle-arena .wrapper-floor-mobs {
        position: relative;
        width: 512px;
        height: 256px;
    }

    .battle-arena .mob-image {
        width: 128px;
        height: 200px;
        position: absolute;
        bottom: 50px;
        left: 50px;
    }

    .battle-arena .enemy-image {
        width: 128px;
        height: 180px;
        position: absolute;
        top: -80px;
        right: 50px;
    }
</style>