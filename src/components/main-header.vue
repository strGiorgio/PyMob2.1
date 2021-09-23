<template>
    <header class="main-container">
        <avatar />
        <login v-show="toggleLogin"/>
        <userProfile v-show="toggleUser" />
    </header>
</template>
<script>
import avatar from './avatar.vue'
import login from './login.vue'
import userProfile from './user-profile.vue'

export default {
    name: 'mainHeader',
    data() {
        return {
            toggleUser: true,
            toggleLogin: true
        }
    },
    components: {
        avatar,
        login,
        userProfile
    },
    methods: {
        toggleUserProfile() {
            this.toggleUser = !this.toggleUser;
            this.toggleLogin = !this.toggleLogin
        }
    }
}
</script>

<style scoped>
    .main-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: var(--color-secondary);
    height: 70px;
    max-height: 100px;
    width: 100%;
    max-width: 1920px;
    position: relative;
    margin: 0 auto;
    padding: 15px;
}

</style>