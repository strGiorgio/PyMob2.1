<template>
    <div class="battle-arena">
        <h1>Welcome to Arena</h1>
        <div class="area">
            <controller />
        </div>
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
    .battle-arena {
        width: 100vw;
        max-width: 1920px;
        min-height: calc(100vh - 70px);
        background-color: var(--color-primary);
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 30px 0 0 0;
        margin: 0 auto;
    }

    .battle-arena h1 {
        font: 2.3rem var(--font-primary);
        text-align: center;
        margin-bottom: 30px;
    }

    .area {
        width: 80%;
        height: 550px;
        background-color: #fff;
        position: relative;
        overflow: hidden;
    }
</style>