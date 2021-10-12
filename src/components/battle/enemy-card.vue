<template>
    <div class="enemy-card">
        <div class="wrapper-name-level">
            <p>EnemyName</p>
            <p>Lv1</p>
        </div>
        

        <div class="wrapper-hp">
            <p>HP:  </p>
            <progress max="100" value="50"></progress>
        </div>
        
    </div>
</template>

<script>
export default {
    name: 'enemyCard'
}
</script>

<style scoped>
    .enemy-card {
        width: 250px;
        height: 70px;
        border: 1px solid var(--color-black-default);
        background-color: var(--color-secondary);
        position: absolute;
        top: 0;
        margin: 10px;
        display: flex;
        flex-direction: column;
        padding: 10px;
    }

    .enemy-card .wrapper-name-level {
        display: flex;
        justify-content: space-between;
    }

    .enemy-card .wrapper-name-level p {
        font: 1.5rem var(--font-primary);
        margin-bottom: 5px;
    }

    .enemy-card .wrapper-hp {
        display: flex;
        background-color: var(--color-gray);
        border-radius: 10px;
        padding: 3px 5px;
    }

    .enemy-card .wrapper-hp progress {
        width: 100%;
        align-self: center;
        border: 1px solid var(--color-black-default);
        border-radius: 10px;
    }

    .enemy-card .wrapper-hp progress::-webkit-progress-bar {
        background-color: #fff;
    }

    .enemy-card .wrapper-hp progress::-moz-progress-bar {
        background-color: var(--color-red-default);
        border-radius: 10px;
    }

    .enemy-card .wrapper-hp progress::-moz-progress-value {
        background-color: var(--color-red-default);
    }

    .enemy-card .wrapper-hp progress::-webkit-progress-value {
        background-color: var(--color-red-default);
    }

    .enemy-card .wrapper-hp p {
        font: 1.3rem var(--font-primary);
        margin: 0;
    }

</style>