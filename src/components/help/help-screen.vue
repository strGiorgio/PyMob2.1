<template>
    <div class="help-screen">
        <h1>How to play</h1>
        
        <router-link class="router-button arrow" to="/">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-arrow-left-circle" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M1 8a7 7 0 1 0 14 0A7 7 0 0 0 1 8zm15 0A8 8 0 1 1 0 8a8 8 0 0 1 16 0zm-4.5-.5a.5.5 0 0 1 0 1H5.707l2.147 2.146a.5.5 0 0 1-.708.708l-3-3a.5.5 0 0 1 0-.708l3-3a.5.5 0 1 1 .708.708L5.707 7.5H11.5z"/>
            </svg>
        </router-link>     
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
        position: relative;
    }

    .help-screen h1 {
        font: 3rem var(--font-primary);
        text-align: center;
        padding: 50px;
    }

    .arrow {
        position: absolute;
        top: 0;
        margin: 50px;
        cursor: pointer;
        color: var(--black-default);
    }

    .arrow:hover {
        transform: scale(1.10);
        opacity: 70%;
    }

    @media (max-width: 768px) {
        .arrow {
            margin: 50px 20px 0;
        }
    }

    @media (max-width: 460px) {
        .arrow {
            margin: 10px 20px 0;
        }
    }
</style>