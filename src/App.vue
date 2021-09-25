<template>
  <div>
    <mainHeader />
    <router-view/>
  </div>
</template>

<script>
import mainHeader from './components/main-header.vue'

export default {
  name: 'App',
  components: {
    mainHeader
  }
}
</script>

<style>
 :root {
    --color-primary: #a84d16;
    --color-primary-light: #cf9571;
    --color-secondary: #5C4D42;
    --color-black-default: #000;
    --color-black-shadow: #2b2b2b;
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
  }
</style>
