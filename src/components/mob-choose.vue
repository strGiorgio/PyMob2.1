<template>
    <div class="container">
        <img src="/img/unknown.png" alt="Your mob apperence">
        <div class="wrapper-buttons">
            <button>Previous</button>
            <button>Next</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'mobChoose'
}
</script>

<style scoped>
    .container {
        border: 2px solid var(--color-black-default);
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
        width: 30%;
        height: 100%;
    }

    .container img {
        width: 100%;
        height: 90%;
    }

    .container .wrapper-buttons {
        width: 100%;
        height: 10%;
    }

    .container .wrapper-buttons button {
        width: 50%;
        height: 100%;
        border: 2px solid var(--color-black-default);
        font: 1rem var(--font-primary);
        background-color: var(--color-secondary);
    }

</style>