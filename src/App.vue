<template>
  <div id="app">
    <img alt="pokemon" src="./assets/pokemon.png" />
    <Pokedex class="poke" msg="Pokeguía" />
  </div>
</template>

<script>
import Pokedex from "./components/Pokedex.vue";

export default {
  name: "App",
  components: {
    Pokedex,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #feca30;
  margin: 0;
  padding: 0;
}

img {
  width: 50%;
  padding-top: 40px;
}

.poke {
  padding-bottom: 80px;
}
</style>
