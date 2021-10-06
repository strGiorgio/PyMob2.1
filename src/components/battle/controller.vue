<template>
    <div class="controller">
        
    </div>
</template>

<script>
export default {
    name: 'controller'
}
</script>

<style scoped>
    .controller {
        width: 300px;
        height: 160px;
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        position: absolute;
        bottom: 10px; 
        right: 200px;
        transform: translateX(450px);
        animation: slideToLeft 2s forwards;
    }

    @keyframes slideToLeft {
        to {
            transform: translateX(0);
        }
    }
</style>