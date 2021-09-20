<template>
    <div class="help-screen">
        <div>
            <h1>How to play</h1>
        </div>
    </div>
</template>

<script>
export default {
    name: 'helpScreen'
}
</script>

<style scoped>
    .help-screen {
        background-color: var(--color-primary);
        width: 100vw;
        max-width: 1920px;
        height: calc(100vh - 70px);
        margin: 0 auto;
    }

    .help-screen h1 {
        font: 3rem var(--font-primary);
    }
</style>