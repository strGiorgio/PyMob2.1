<template>
  <div class="home">
    <mainMenu />
  </div>
</template>

<script>
// @ is an alias to /src
import mainMenu from '../components/menu/main-menu.vue'

export default {
  name: 'home',
  components: {
    mainMenu
  }
}
</script>
