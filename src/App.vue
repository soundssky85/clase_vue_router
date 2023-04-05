<template>
    <Navbar />
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <AboutPage></AboutPage> -->

  <router-view />
</template>

<script>

import {defineAsyncComponent} from 'vue'


/* import AboutPage from '@/modules/pokemon/pages/PokemonPage.vue' */

export default {
  name: 'App',
  components: {
     Navbar: defineAsyncComponent(() => import(/*webpackChunkName: "Navbar" */ "@/modules/shared/components/Navbar"))
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
