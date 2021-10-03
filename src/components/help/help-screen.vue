<template>
    <div class="help-screen">
        <h1>How to play</h1>
        <helpBox />
    </div>
</template>

<script>
import helpBox from './help-box';

export default {
    name: 'helpScreen',
    components: {
        helpBox
    }
}
</script>

<style scoped>
    .help-screen {
        background-color: var(--color-primary);
        width: 100vw;
        max-width: 1920px;
        min-height: calc(100vh - 70px);
        margin: 0 auto;
    }

    .help-screen h1 {
        font: 3rem var(--font-primary);
        text-align: center;
        padding: 50px;
    }
</style>