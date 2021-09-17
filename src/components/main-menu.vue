<template>
    <div class="main-container">
        <h1>PyMob 2.1</h1>
        <div class="wrapper-buttons">
            <button><router-link to="/Home">New Game</router-link></button>
            <button><router-link to="/About">How to play</router-link></button>
        </div>
    </div>
</template>

<script>
export default {
    name: "mainMenu"
}
</script>

<style scoped>
    .main-container {   
        background-color: var(--color-primary);
        width: 100vw;
        max-width: 1920px;
        height: calc(100vh - 70px);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
        margin: 0 auto;
    }

    .main-container h1{
        font-size: 11rem;
        font-family: var(--font-primary);
        text-shadow: 5px 5px 1px var(--color-black-shadow);
        margin-bottom: 40px;
        color: var(--color-black-default);
    }

    .main-container .wrapper-buttons {
        width: 70%;
    }

    .main-container button {
        width: 100%;
        height: 40px;
        font-size: 1.5rem;
        font-family: var(--font-primary);
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        margin: 5px;
        transition: .2s;
    }

    .main-container button a {
        text-decoration: none;
        color: var(--color-black-default);
    }

    .main-container button:hover {
        transform: scale(1.02);
    }

    @keyframes fontAnimation {
        0% {
            font-size: 10rem;
        }
        50% {
            font-size: 11rem;
        }
        100% {
            font-size: 10rem;
        }
    }
</style>