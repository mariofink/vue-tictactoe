<template>
  <div>
    <div class="board-row">
      <square index="0" :value="squares[0]" @selection="onSquareSelection"></square>
      <square index="1" :value="squares[1]" @selection="onSquareSelection"></square>
      <square index="2" :value="squares[2]" @selection="onSquareSelection"></square>
    </div>
    <div class="board-row">
      <square index="3" :value="squares[3]" @selection="onSquareSelection"></square>
      <square index="4" :value="squares[4]" @selection="onSquareSelection"></square>
      <square index="5" :value="squares[5]" @selection="onSquareSelection"></square>
    </div>
    <div class="board-row">
      <square index="6" :value="squares[6]" @selection="onSquareSelection"></square>
      <square index="7" :value="squares[7]" @selection="onSquareSelection"></square>
      <square index="8" :value="squares[8]" @selection="onSquareSelection"></square>
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
