<template>
    <div class="main-menu">
        <h1>PyMob 2.1</h1>
        <div class="wrapper-buttons">
            <router-link class="router-button" to="/new_game">New Game</router-link>
            <router-link class="router-button" to="/help">How to play</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: "mainMenu"
}
</script>

<style scoped>
    .main-menu {   
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

    .main-menu h1{
        font-size: 11rem;
        font-family: var(--font-primary);
        text-shadow: 5px 5px 1px var(--color-black-shadow);
        margin-bottom: 40px;
        color: var(--color-black-default);
    }

    .main-menu .wrapper-buttons {
        width: 70%;
    }

    .main-menu .router-button {
        width: 100%;
        padding: 10px;
        font-size: 1.5rem;
        font-family: var(--font-primary);
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        margin-bottom: 5px;
        transition: .2s;
        text-decoration: none;
        color: var(--color-black-default);
        display: block;
        text-align: center;
    }

    .main-menu .router-button:hover {
        transform: scale(1.02);
    }

    @media (max-width: 1024px) {
        .main-menu h1 {
            font-size: 7rem;
        }
    }

    @media (max-width: 640px) {
        .main-menu h1 {
            font-size: 5rem;
            text-align: center;
        }
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