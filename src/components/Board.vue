<template>
  <div>
    <div class="board-row">
      <square></square>
      <square></square>
      <square></square>
    </div>
    <div class="board-row">
      <square></square>
      <square></square>
      <square></square>
    </div>
    <div class="board-row">
      <square></square>
      <square></square>
      <square></square>
    </div>
  </div>
</template>

<script>
import Square from "./Square.vue";

export default {
  name: "board",
  components: {
    Square
  }
};
</script>
