<template>
    <div class="controller">
        <div class="wrapper-img">
            <img src="/img/avatar.png" alt="">
        </div>
        <div class="controller-buttons">
            <progress id="progress-bar" max="100" value="50"></progress>
            <span>HP: 10 / 100</span>
            <button>Atack</button>
            <button>Atack Especial</button>
            <button>Escape</button>
            <button>Regenerate</button>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'controller'
}
</script>

<style scoped>
    .controller {
        width: 450px;
        height: 160px;
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        position: absolute;
        bottom: 10px; 
        right: 200px;
        transform: translateX(450px);
        animation: slideToLeft 2s forwards;
        padding: 5px;
        display: grid;
        grid-template-columns: 1.3fr 2fr;
        
    }

    .wrapper-img img{
        width: 90%;
        height: 100%;
    }

    .controller-buttons {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr fr;
        grid-gap: 5px;
    }
    
    .controller-buttons progress {
        width: 100%;
        border: 0px solid var(--color-black-default);
        grid-column: 1 / 3;
        position: relative;
    }

    .controller-buttons progress::-webkit-progress-bar {
        background-color: var(--color-white-default);
        height: 35px;
    }
    
    .controller-buttons progress::-moz-progress-bar {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons progress::-webkit-progress-value {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons progress::-moz-progress-value {
        background-color: var(--color-green-secondary);
    }

    .controller-buttons span {
        font: 1.3rem var(--font-primary);
        position: absolute;
        right: 60px;
        top: 17px;
    }

    .controller-buttons button {
        background-color: var(--color-gray);
        border: 2px solid var(--color-black-default);
        font: 1rem var(--font-primary);
        transition: .5s;
    }

    .controller-buttons button:hover {
        opacity: 70%;
    }

    @keyframes slideToLeft {
        to {
            transform: translateX(0);
        }
    }
</style>