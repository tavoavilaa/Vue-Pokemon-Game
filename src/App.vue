<template>
  <PokemonPage/>
</template>

<script>

import PokemonPage from "@/pages/PokemonPage";


export default {
  name: 'App',
  components: {
    PokemonPage,
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
