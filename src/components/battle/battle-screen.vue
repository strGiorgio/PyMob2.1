<template>
    <div class="container">
        <controller />
    </div>
</template>

<script>
import controller from './controller.vue'
export default {
    name: 'battleScreen',
    components: {
        controller
    }
}
</script>

<style scoped>
    .container {
        width: 100vw;
        max-width: 1920px;
        min-height: calc(100vh - 70px);
        background-color: var(--color-primary);
    }
</style>