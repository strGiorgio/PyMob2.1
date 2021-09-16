<template>
  <div id="nav">
    <router-link to="/Home">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style>
 :root {
    --color-primary: #a84d16;
    --color-secondary: #5C4D42;
    --color-black-default: #000;
    --color-black-shadow: #2b2b2b;
    --color-white-default: #fff;
    --color-green-default: lime;
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
