<template>
    <form class="change-avatar" @submit="sendToDB($event)">
        <div class="close-button" @click="$emit('closed')">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="#000000" class="bi bi-x" viewBox="0 0 16 16">
            <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/>
            </svg>
        </div>
        <input type="url" required min="2" v-model="url" placeholder="Ex: https://i.imgur.com/perros" title="You can put a url to change your user avatar">
        <input type="submit" value="change avatar">
    </form>
</template>

<script>
export default {
    name: 'changeAvatar',
    data() {
        return {
            url: null
        }
    },
    emits: ['closed'],
    methods: {
        async sendToDB(e) {
            e.preventDefault()

            //Find user logado in users database
            const logadosDB = await fetch('http://localhost:3000/logado');
            const logados = await logadosDB.json()

            const usersDB = await fetch('http://localhost:3000/users');
            const users = await usersDB.json()
            //Create var id
            var id = null
            //Veriy user, if equal id = user id
            for (var i in users) {
                if (logados[0].name == users[i].name && logados[0].passwd == users[i].passwd) {
                    id = users[i].id
                }
            }
            //Put url in user database
            const data = JSON.stringify({avatar: this.url})
            await fetch(`http://localhost:3000/users/${id}`, {
                method: 'PATCH',
                headers: {"Content-Type": "application/json"},
                body: data
            });
            console.log(this.url)

            setTimeout(() => {window.location.reload()}, 500)
        }
    }
}
</script>

<style scoped>
    .change-avatar {
        display: flex;
        flex-direction: column;
        background-color: var(--color-primary);
        border: 2px solid var(--color-black-default);
        width: 500px;
        padding: 30px 50px;
        

        position: absolute;
        top: calc(50vh - 100px);
        right: calc(50vw - 200px);
        z-index: 10;
    }

    .change-avatar .close-button {
        position: absolute;
        top: 5px;
        right: 5px;
        cursor: pointer;
    }

    .change-avatar .close-button:hover {
        opacity: 60%;
    }

    .change-avatar input {
        width: 100%;
        padding: 5px 0;
        font: 1.2rem "Press Start 2P", cursive;
    }

    .change-avatar input[type="submit"] {
        margin-top: 10px;
        font: 1.3rem "Press Start 2P", cursive;
        background-color: var(--color-secondary);
        padding: 5px 0;
        border: 1.5px solid var(--color-black-default);
        transition: .3s;
    }

    .change-avatar input[type="submit"]:hover {
        transform: scale(1.03);
    }
</style>