<template>
    <div class="moldure">
        <img class="img-avatar" :src="img" :alt="description">
    </div>
</template>
<script>
export default {
    name: 'avatar',
    data() {
        return {
            img: '/img/avatar.png',
            description: 'Ursinho Balaclava'
        }
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
    }

    .img-avatar {
        width: 100%;
        height: 100%;
    }

</style>