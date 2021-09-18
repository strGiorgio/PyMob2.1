<template>
    <header class="main-container">
        <avatar />
        <login v-show="true" />
        <userProfile v-show="false"/>
    </header>
</template>
<script>
import avatar from './avatar.vue'
import login from './login.vue'
import userProfile from './user-profile.vue'

export default {
    name: 'mainHeader',
    components: {
        avatar,
        login,
        userProfile
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