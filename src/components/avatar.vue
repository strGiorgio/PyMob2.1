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
            img: '/img/unknown.png',
            description: 'Ursinho Balaclava'
        }
    }
}
</script>

<style scoped>
    .moldure {
        width: 50px;
        height: 50px;
        background-color: var(--color-white-default);
        border: 3px solid var(--color-black-default);
        overflow: hidden;
    }

    .img-avatar {
        width: 50px;
        height: 50px;
    }

</style>