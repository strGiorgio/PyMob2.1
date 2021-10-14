<template>
    <div>
        <nav>
            <ul>
                <li class="list-1 active" @click="btnLeftIsPressed">Attributes, points...</li>
                <li class="list-2" @click="btnRightIsPressed">Battle</li>
            </ul>
        </nav>

        <div class="container">
            <div class="help-attributes" v-show="showAttributesHelp">
                <h2>Attributes, Points and Level</h2>
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

            <div class="help-battle" v-show="showBattleHelp">
                <h2>Battle</h2>
                <article>
                    <h3>Batalha</h3>
                    <p>Na arena você terá 4 ações. Atacar, ataque especial, regenerar e fugir. O jogador terá uma rodada por vez, podendo escolher sua ação, sendo assim, você só pode atacar ou regenerar por cada vez separadamente. Escolha a ação certa!</p>
                </article>

                <article>
                    <h3>Atacar</h3>
                    <p>Caso ataque, seu hit no inimigo será sua força multiplicada pela estamina.</p>
                </article>

                <article>
                    <h3>Ataque Especial</h3>
                    <p>O ataque especial, raramente poderá ser usado, mas quando usado, da 1.5x de dano ao enimigo.</p>
                </article>

                <article>
                    <h3>Regenerar</h3>
                    <p>Sua regeneração é sua defesa multiplicado por sua estamina, lembrando que quando maior a estamina, mais rápido será sua regeneração.</p>
                </article>

                <article>
                    <h3>Fugir</h3>
                    <p>Caso decida fugir, você não ganhará nenhum ponto e seu level não subirá, lembrando que pode haver a chance de seu mob não conseguir fugir, caso sua estamina esteja baixa.</p>
                </article>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'helpBox',
    data() {
        return {
            showAttributesHelp: true,
            showBattleHelp: false
        }
    },
    methods: {
        btnLeftIsPressed() {
            const btn1 = document.querySelector('.list-1');
            const btn2 = document.querySelector('.list-2');

            btn1.classList.add('active')
            btn2.classList.remove('active')

            this.showAttributesHelp= true,
            this.showBattleHelp = false
        },
        
        btnRightIsPressed() {
            const btn1 = document.querySelector('.list-1');
            const btn2 = document.querySelector('.list-2');

            btn2.classList.add('active')
            btn1.classList.remove('active')

            this.showAttributesHelp= false,
            this.showBattleHelp = true
        }
    }
}
</script>

<style scoped>
    .container {
        border: 2px solid var(--color-black-default);
        width: 60%;
        height: 60%;
    }

    nav {
        font: 1.4rem var(--font-primary);
        width: 60%;
        margin: 0 auto;
    }

    nav ul{
        list-style-type: none;
        display: flex;
        width: 100%;
        justify-content: space-evenly;
        margin: 0;
        padding: 0;
        width: 100%;
        cursor: pointer;
    }

    nav ul li {
        padding: 5px 20px;
        width: 100%;
        transition: .5s;
    }

    nav ul li:hover {
        background-color: var(--color-secondary);
    }

    nav ul .active {
        background-color: var(--color-secondary);
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