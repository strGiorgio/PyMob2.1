<template>
    <header class="main-container">
        <avatar />
        <login />
    </header>
</template>
<script>
import avatar from './avatar.vue'
import login from './login.vue'

export default {
    name: 'mainHeader',
    components: {
        avatar,
        login
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
}

</style>