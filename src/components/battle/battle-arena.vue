<template>
    <div class="battle-arena">
        <div class="wrapper-floor-mobs">
            <img class="floor-arena" src="/img/arena.png" alt="Floor arena">

            <!-- Mobs -->
            <img class="mob-image" src="/img/tartaruga-idle.png" alt="">

            <!-- Enemies -->
            <img class="enemy-image" src="/img/morcego.png" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'battleArena'
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