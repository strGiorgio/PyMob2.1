<template>
    <div class="wrapper-attr">
        <div class="first-wrapper">
            <label>Level:</label>
            <label>Points:</label>
        </div>
        <label>HP:</label>
        <label>Defense:</label>
        <label>Stamina:</label>
        <label>Strenght:</label>

        <button>Start battle</button>
    </div>
</template>
<script>
export default {
    name: 'mobAttributes'
}
</script>

<style scoped>
    .wrapper-attr {
        width: 70%;
        height: 100%;
        padding: 50px;
        font: 2rem var(--font-primary);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .wrapper-attr .first-wrapper {
        display: flex;
        justify-content: space-around;
    }

    .wrapper-attr button {
        width: 40%;
        padding: 30px 20px;
        background-color: var(--color-green-default);
        border: 2px solid var(--color-black-default);
        align-self: end;
    }

</style>