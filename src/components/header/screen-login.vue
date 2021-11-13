<template>
    <form class="form-container" @submit="submited($event), $emit('logged')">
        <div class="close-button" @click="$emit('closeButton')">
            <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-x" viewBox="0 0 16 16">
            <path d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/>
            </svg>
        </div>

        <p>{{ msg }}</p>

        <label for="name">Name:</label>
        <input id="name" type="text" placeholder="Your name here..." minlength="2" maxlength="24" v-model="name">

        <label for="passwd">Password:</label>
        <input id="passwd" type="password" placeholder="Your password here..." minlength="2" maxlength="6" v-model="passwd"> 

        <div class="wrapper-buttons">
            <input class="btn-submit" @click="logIn" type="submit" value="Sign In">
            <input class="btn-submit" @click="signUp" type="submit" value="Sign Up">
        </div>
    </form>
</template>

<script>
export default {
    name: 'screenLogin',
    data() {
        return {
            showScreen: false,
            name: null,
            passwd: null,
            msg: null
        }
    },
    emits: ['closeButton', 'logged'],
    methods: {
        submited(e) {
            e.preventDefault()
        },
        async logIn() {
            const user = {
                name: this.name,
                passwd: this.passwd
            }

            const req = await fetch('http://localhost:3000/users');
            const data = await req.json();

            for (var i in data) {
                if (data[i].name == user.name) {
                    console.log('Nome encontrado!')
                    if (data[i].passwd === user.passwd) {
                        console.log('Senha compátivel!')
                        //Deleta user logado do banco de dados
                        this.deleteUserLogged()

                        //Add user logado no banco logado
                        const reqAdduser = await fetch('http://localhost:3000/logado', {
                            method: 'POST',
                            headers: {
                                "content-Type" : "application/json",
                            },
                            body: JSON.stringify(user)
                        })

                        const res = reqAdduser.json()
                        console.log(res)

                        //Limpa campos
                        this.name = ''
                        this.passwd = ''

                        //Muda mensagens e a cor
                        const paragraph = document.querySelector(".form-container p");
                        paragraph.style.color = 'var(--color-green-default)'

                        this.msg = "Logado!"
                    } else {
                        const paragraph = document.querySelector(".form-container p");
                        paragraph.style.color = 'var(--color-red-default)'
                        this.msg = "Senha ou usuário incorretos!"
                    }
                }

                setTimeout(() => {this.msg = null}, 3000)
            }
        },

        async signUp() {
            const user = {
                name: this.name, 
                passwd: this.passwd,
                avatar: '/img/avatar.png'
            }

            const req = await fetch('http://localhost:3000/users')
            const data = await req.json()

            for (var i in data) {
                var UserExist = false
                if (data[i].name == user.name) {
                    console.log('User name already exists!')
                    UserExist = true
                    break
                } else {
                    console.log(`Verified users accounts: ${i}`)
                }
            }

            if (!UserExist) {
                //Turn user in a JSON stringify
                var dataJson = JSON.stringify(user)
                const paragraph = document.querySelector(".form-container p");
                
                //Insert user in database
                const req = await fetch('http://localhost:3000/users', {
                    method: "POST",
                    headers: { "Content-Type" : "application/json"},
                    body: dataJson
                })

                const res = await req.json()
                paragraph.style.color = 'var(--color-green-default)'
                this.msg = "Usuário cadastrado!"
                console.log(res)

                //Generate mob
                const mob = {
                    owner: this.name,
                    owner_passwd: this.passwd,
                    hp: 20,
                    defense: 10,
                    strength: 5,
                    stamina: 5,
                    level: 0,
                    points: 0,
                    mob_appearance: 0
                }
                //Add a mob in database
                const mobJson = JSON.stringify(mob);
                const mobReq = await fetch('http://localhost:3000/mobs', {
                    method: 'POST',
                    headers: {"Content-Type": "application/json"},
                    body: mobJson
                });
                const mobRes = await mobReq.json()
                console.log(mobRes)

            } else {
                const paragraph = document.querySelector(".form-container p");
                paragraph.style.color = 'var(--color-red-default)';
                this.msg = "Usuário já existe!"
            }



            this.name = ""
            this.passwd = ""
            setTimeout(()=> {this.msg = null}, 3000)
        },

        async deleteUserLogged() {
            const req = await fetch('http://localhost:3000/logado');
            const data = await req.json();

            const reqDelete = await fetch(`http://localhost:3000/logado/${data[0].id}`, {
                method: 'DELETE'
            })
            const res = reqDelete.json()
            console.log(res)
        }
    }
}
</script>

<style scoped>
    .form-container {
        background-color: var(--color-primary);
        min-width: 400px;
        display: flex;
        flex-direction: column;
        border: 2px solid var(--color-black-default);
        padding: 30px;
        position: absolute;
        top: calc(50vh - 100px);
        right: calc(50vw - 200px);
        z-index: 10;
    }

    .form-container .close-button {
        position: absolute;
        top: 0;
        right: 0px;
        transition: .2s;
    }

    .form-container .close-button:hover {
        opacity: 50%;
    }

    .form-container p {
        font: 1rem var(--font-primary);
        text-align: center;
        color: var(--color-green-default);
    }

    .form-container input {
        font: 1.2rem var(--font-primary);
        margin-bottom: 10px;
        background-color: var(--color-white-default);
        outline-color: red;
    }

    .form-container label {
        font: 1.8rem var(--font-primary);
        margin-bottom: 5px;
        color: var(--color-black-default);
    }

    .form-container .btn-submit {
        font: 1.5rem var(--font-primary);
        background-color: var(--color-secondary);
        border: 2px solid var(--color-black-default);
        margin-top: 15px;
        transition: .2s;
        padding: 5px 20px;
    }

    .form-container .btn-submit:hover {
        transform: scale(1.02);
    }

    .form-container .wrapper-buttons {
        display: flex;
        justify-content: space-around;
    }
</style>