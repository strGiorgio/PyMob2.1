<template>
    <div class="attributes-screen">
        <h1>YOUR MOB:</h1>
        <div class="wrapper-attributes">
            <mobChoose />
            <mobAttribute />
        </div>
    </div>
</template>

<script>
import mobChoose from './mob-choose'
import mobAttribute from './mob-attributes'

export default {
    name: 'attributesScreen',
    components: {
        mobChoose,
        mobAttribute
    }
}
</script>

<style scoped>
    .attributes-screen {
        background-color: var(--color-primary);
        width: 100vw;
        max-width: 1920px;
        height: calc(100vh - 70px);
        margin: 0 auto;
    }

    .attributes-screen h1 {
        font: 3rem var(--font-primary);
        text-align: center;
        padding: 50px;
    }

    .attributes-screen .wrapper-attributes {
        border: 5px solid var(--color-black-default);
        width: 90%;
        max-width: 1920px;
        height: 70%;
        max-height: 1080px;
        margin: 0 auto;
        display: flex;
    }
</style>
