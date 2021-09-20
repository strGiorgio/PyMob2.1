<template>
    <div class="attributes-screen">
        <h1>WELCOME!</h1>
    </div>
</template>

<script>
export default {
    name: 'attributesScreen'    
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
    }
</style>
