<template>
    <div class="controller">
        <div class="wrapper-img">
            <img src="/img/avatar.png" alt="">
        </div>
        <div class="controller-buttons">
            <progress max="100" value="10" ></progress>
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
        grid-column: 1 / 3;
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