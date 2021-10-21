<template>
    <div class="user-profile">
        <ul>
            <li><a href="#">{{ user }} <span><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-caret-down-fill" viewBox="0 0 16 16">
            <path d="M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z"/>
            </svg></span></a>
            <ul>
                <li><a href="#">Config</a></li>
                <li><a href="#">Change Avatar</a></li>
                <hr>
                <li><a href="#" @click="logout">Logout</a></li>
            </ul>
            </li>
        </ul>
        
    </div>
</template>

<script>
export default {
    name: 'userProfile',
    data() {
        return {
            user: null
        }
    },
    methods: {
        async getUser() {
            const url = 'http://localhost:3000/logado';
            const req = await fetch(url)
            const res = await req.json();
            this.user = res[0].name
        },

        async logout() {
            const data = {
                name: null,
                passwd: null
            }

            //Get user logged and delete 
            const reqLoggedDB = await fetch('http://localhost:3000/logado');
            const resLoggedDB = await reqLoggedDB.json();

            const delUserLogged = await fetch(`http://localhost:3000/logado/${resLoggedDB[0].id}`, {
                method: 'DELETE'
            });


            //Add a empty user
            const loggedDb = await fetch('http://localhost:3000/logado', {
                method: 'POST',
                headers: {"Content-Type" : "application/json"},
                body: JSON.stringify(data)
            })
            const user = await loggedDb.json()
            
            console.log('logout', resLoggedDB, delUserLogged, user)
            document.location.reload(true)
        }
    },
    mounted() {
        this.getUser()
    }
}
</script>

<style scoped>
    .user-profile ul{
        background-color: var(--color-primary);
        border: 2px solid var(--color-black-default);
        font: 1.3rem var(--font-primary);
        margin: 0;
        padding: 10px;
        position: relative;
        list-style-type: none;
    }

    .user-profile ul li {
        text-align: left;
        display: inline-block;
    }

    .user-profile ul li a{
        color: var(--color-black-default);
        text-decoration: none;
    }
    
    .user-profile ul li a span svg {
        transition: .5s;
    }

    .user-profile ul:hover li a span svg {
        transform: rotate(180deg);
    }

    .user-profile ul ul {
        display: none;
        position: absolute;
        top: 100%;
        right: 0;
        z-index: 10;
    }

    .user-profile ul ul li{
        width: 100%;
        padding: 5px 0;
    }

    .user-profile ul ul li:hover {
        background-color: var(--color-primary-light);
    }

    .user-profile ul:hover li ul {
        display: block;
    }
    
</style>