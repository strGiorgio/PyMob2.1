<template>
  <div class="home">
    <mainMenu />
  </div>
</template>

<script>
// @ is an alias to /src
import mainMenu from '../components/main-menu.vue'

export default {
  name: 'Home',
  components: {
    mainMenu
  }
}
</script>
