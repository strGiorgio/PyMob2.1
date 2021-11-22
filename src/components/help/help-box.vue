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
                    <p>Every mob starts with 20 HP which is your hit points.</p>
                </article>

                <article>
                    <h3>DEFENSE:</h3>
                    <p>Every mob starts with 5 defense, the defense subtracts enemy damage, meaning if you take 30 damage, you'll be deacityd 5, taking 25 damage.</p>
                </article>

                <article>
                    <h3>STRENGTH:</h3>
                    <p>Every mob starts with 5 strength, its strength is multiplied by its stamina.</p>
                </article>

                <article>
                    <h3>ESTAMINA:</h3>
                    <p>Every mob starts with 1 stamina. Stamina serves to regenerate your mob faster and increase total damage.</p>
                </article>

                <div class="points-level"> 
                    <article>
                        <h3>Level</h3>
                        <p>At each level, you will face new enemies. The higher your level, the harder it will be!</p>
                    </article>

                    <article>
                        <h3>Points</h3>
                        <p>Your points can be exchanged for more attributes. To earn points you need to win battles.</p>
                    </article>
                </div>
            </div>

            <div class="help-battle" v-show="showBattleHelp">
                <h2>Battle</h2>
                <article>
                    <h3>Battle</h3>
                    <p>In the arena you will have 4 shares. Attack, special attack, regenerate and escape. The player will have one round at a time, being able to choose their action, so you can only attack or regenerate each time separately. Choose the right action!</p>
                </article>

                <article>
                    <h3>Attack</h3>
                    <p>Caso ataque, seu hit no inimigo será sua força multiplicada pela estamina.</p>
                </article>

                <article>
                    <h3>Especial Attack</h3>
                    <p>If you attack, your hit on the enemy will be your strength multiplied by stamina.</p>
                </article>

                <article>
                    <h3>Regenerate</h3>
                    <p>Its regeneration is its defense multiplied by its stamina, remembering that the greater the stamina, the faster its regeneration will be.</p>
                </article>

                <article>
                    <h3>Flee</h3>
                    <p>If you decide to run, you won't earn any points and your level won't go up, remembering that there may be a chance your mob won't be able to escape if your stamina is low.</p>
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