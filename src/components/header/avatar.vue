<template>
    <div class="moldure">
        
    </div>
</template>

<script>
export default {
    name: 'avatar',
    data() {
        return {
            avatar: null,
            description: 'Ursinho Balaclava'
        }
    },
    methods: {
        async getAvatar() {
            const dbLogado = await fetch('http://localhost:3000/logado');
            const logado = await dbLogado.json();

            const dbUsers = await fetch('http://localhost:3000/users');
            const users = await dbUsers.json()

            for (var i in users) {
                if (logado[0].name == users[i].name && logado[0].passwd == users[i].passwd) {
                    //Pega o avatar no banco de dados e muda avatar do usuário na tela
                    const moldure = document.querySelector('.moldure');
                    this.avatar = users[i].avatar
                    console.log(`Your avatar: ${this.avatar}`)
                    moldure.style.backgroundImage = `url(${this.avatar})`;
                    break
                }
            }

            
        }
    },
    mounted() {
        this.getAvatar()
    }
}
</script>

<style scoped>
    .moldure {
        width: 50px;
        height: 50px;
        border: 2px solid var(--color-black-default);
        overflow: hidden;
        box-sizing: border-box;
        
        background-size: cover ;
    }

    .img-avatar {
        width: 100%;
        height: 100%;
    }

</style>