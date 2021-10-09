<template>
    <div class="battle-screen">
        <h1>Welcome to Arena</h1>
        <div class="wrapper-arena">
            <battleArena />
            <enemyCard />
            <controller />
        </div>
    </div>
</template>

<script>
import battleArena from './battle-arena.vue'
import enemyCard from './enemy-card.vue'
import controller from './controller.vue'

export default {
    name: 'battleScreen',
    components: {
        battleArena,
        controller,
        enemyCard
    }
}
</script>

<style scoped>
    .battle-screen {
        width: 100vw;
        max-width: 1920px;
        height: calc(100vh - 70px);
        background-color: var(--color-primary);
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 30px 0 0 0;
        margin: 0 auto;
    }

    .battle-screen h1 {
        font: 2.3rem var(--font-primary);
        text-align: center;
        margin-bottom: 30px;
    }

    .battle-screen .wrapper-arena {
        width: 70%;
        height: 80%;
        max-height: 1080px;
        background-color: #fff;
        position: relative;
        overflow: hidden;
        border: 2px solid var(--color-black-default);
    }
</style>