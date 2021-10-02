<template>
    <div class="container">
        <h2>Attributes, Points e Level</h2>
        <article>
            <h3>HP:</h3>
            <p>Todo mob inicia com 20 de HP que é seus pontos de vida.</p>
        </article>

        <article>
            <h3>DEFENSE:</h3>
            <p>Todo mob inicia com 5 de defesa, a defesa subtrai o dano inimigo, ou seja, caso você receba 30 de dano, será descontado 5, recebendo 25 de dano.</p>
        </article>

        <article>
            <h3>STRENGTH:</h3>
            <p>Todo mob inicia com 5 de força, sua força é multiplicada por sua estamina.</p>
        </article>

        <article>
            <h3>ESTAMINA:</h3>
            <p>Todo mob inicia com 1 de estamina. A estamina serve para regenerar seu mob mais rapido e aumentar ao dano total.</p>
        </article>

        <div class="points-level"> 
            <article>
                <h3>Level</h3>
                <p>A cada level, você enfrentará novos inimigos. Quanto maior seu level, mais difícil será!</p>
            </article>

            <article>
                <h3>Points</h3>
                <p>Seus pontos poderam ser trocados por mais atributos. Para ganhar pontos você precisa ganhar batalhas.</p>
            </article>
        </div>
    </div>
</template>

<script>
export default {
    name: 'helpBox'
}
</script>

<style scoped>
    .container {
        border: 2px solid var(--color-black-default);
        width: 60%;
        height: 60%;
    }

    .container h2 {
        font: 2rem var(--font-primary);
        color: var(--color-black-default);
        text-align: center;
        padding: 10px 0;
    }

    .container article {
        padding: 10px;
    }

    .container .points-level {
        display: flex;
        justify-content: space-around;
    }

    .container h3 {
        font: 1.5rem var(--font-primary);
        color: var(--color-black-default);
    }

    .container p {
        font: 1rem var(--font-primary);
        color: var(--color-black-shadow);
    }

</style>