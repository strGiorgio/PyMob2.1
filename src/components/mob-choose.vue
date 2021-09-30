<template>
    <div class="container">
        <img src="/img/morcego.png" alt="Your mob apperence" v-show="show_img1">
        <img src="/img/tartaruga.png" alt="Your mob apperence" v-show="show_img2">
        <img src="/img/urso.png" alt="Your mob apperence" v-show="show_img3">
        <div class="wrapper-buttons">
            <button @click="slideMobs('previous')">Previous</button>
            <button @click="slideMobs('next')">Next</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'mobChoose',
    data() {
        return {
            show_img1: true,
            show_img2: false,
            show_img3: false,
            n: 0
        }
    },
    methods: {
        slideMobs(direction) {
    
            if (direction == 'next') {
                this.n++
                if (this.n == 3) {
                    this.n = 0
                }
            }else if (direction == 'previous') {
                this.n--
                if (this.n == -1) {
                    this.n = 2
                }
            }

            switch (this.n) {
                case 0:
                    this.show_img1 = true;
                    this.show_img2 = false;
                    this.show_img3 = false;
                    break
                case 1:
                    this.show_img1 = false;
                    this.show_img2 = true;
                    this.show_img3 = false;
                    break
                case 2:
                    this.show_img1 = false;
                    this.show_img2 = false;
                    this.show_img3 = true;
                    break
                default:
                    break
            }
        }
    }
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