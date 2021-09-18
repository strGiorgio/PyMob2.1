<template>
    <div class="wrapper-login">
        <a href="#" @click="show">LogIn</a>
        <a href="#" @click="show">SignUp</a>

        <screenLogin v-show="showScreen" @closeButton="closeButton"/>
    </div>
</template>
<script>
import screenLogin from './screen-login.vue'

export default {
    name: "login",
    data() {
        return {
            showScreen: false
        }
    },
    components: {
        screenLogin
    },
    methods: {
        show () {
            this.showScreen = true
            console.log('Opened')
        },
        closeButton() {
            this.showScreen = false
            console.log('Closed')
        }
    }
}
</script>

<style scoped>
    .wrapper-login a{
        font-size: 1.4rem;
        font-family: var(--font-primary);
        color: var(--color-black-default);
        text-decoration: none;
        margin-right: 15px;
    }

    .wrapper-login a:hover {
        text-decoration: underline;
    }
</style>