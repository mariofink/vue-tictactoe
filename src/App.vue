<template>
  <div id="app">
    <game></game>
  </div>
</template>

<script>
import Game from "./components/Game.vue";
require("./style.css");

export default {
  name: "app",
  components: {
    Game
  }
};
</script>

<style>
</style>
