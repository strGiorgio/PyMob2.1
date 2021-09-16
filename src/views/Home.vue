<template>
  <div class="home">
    <mainHeader />
    <mainMenu />
  </div>
</template>

<script>
// @ is an alias to /src
import mainHeader from '../components/main-header.vue'
import mainMenu from '../components/main-menu.vue'

export default {
  name: 'Home',
  components: {
    mainHeader,
    mainMenu
  }
}
</script>
