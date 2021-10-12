<template>
  <div>
    <mainHeader />
    <router-view/>
  </div>
</template>

<script>
import mainHeader from './components/header/main-header.vue'

export default {
  name: 'App',
  components: {
    mainHeader
  },
  mounted() {
    //window.confirm('Para uma melhor experiência, por favor utilize navegadores mozilla (firefox)')
  }
}
</script>

<style>
 :root {
    --color-primary: #a84d16;
    --color-primary-light: #cf9571;
    --color-secondary: #5C4D42;
    --color-secondary-shadow: #3b322b;
    --color-black-default: #000;
    --color-black-shadow: #2b2b2b;
    --color-gray: #818181;
    --color-white-default: #fff;
    --color-green-default: lime;
    --color-green-secondary: #05be05;
    --color-red-default: #920808;

    --font-primary: "Press Start 2P", cursive;
  }

  html {
  font-size: 10px;
  }

  * {
    padding: 0;
    margin: 0;
  }

  body {
    background-color: var(--color-secondary);
    overflow-x: hidden;
  }
</style>
