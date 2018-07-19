<template>
  <div>
    <div class="board-row">
      <square index="0" @selection="onSquareSelection"></square>
      <square index="1" @selection="onSquareSelection"></square>
      <square index="2" @selection="onSquareSelection"></square>
    </div>
    <div class="board-row">
      <square index="3" @selection="onSquareSelection"></square>
      <square index="4" @selection="onSquareSelection"></square>
      <square index="5" @selection="onSquareSelection"></square>
    </div>
    <div class="board-row">
      <square index="6" @selection="onSquareSelection"></square>
      <square index="7" @selection="onSquareSelection"></square>
      <square index="8" @selection="onSquareSelection"></square>
    </div>
  </div>
</template>

<script>
import Square from "./Square.vue";

export default {
  name: "board",
  components: {
    Square
  },
  props: ["squares"],
  methods: {
    onSquareSelection(event) {
      this.$emit("squareSelection", event);
    }
  }
};
</script>
