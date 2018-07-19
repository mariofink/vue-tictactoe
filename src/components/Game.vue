<template>
  <div>
    <h1>Tic Tac Toe</h1>
    <board></board>
  </div>
</template>

<script>
import Board from "./Board.vue";

export default {
  name: "game",
  components: {
    Board
  }
};
</script>