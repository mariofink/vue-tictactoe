<template>
  <div>
    <h1>Tic Tac Toe</h1>
    <div class="game">
      <div class="game-board">
        <board :squares="current.squares" @squareSelection="onSquareSelection"></board>
      </div>
      <div class="game-info">
        <p>Next player: {{player}}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Board from "./Board.vue";

export default {
  name: "game",
  components: {
    Board
  },
  data: () => {
    return {
      history: [
        {
          squares: Array(9).fill(null)
        }
      ],
      xIsNext: true,
      stepNumber: 0
    };
  },
  computed: {
    current: function() {
      return this.history[this.stepNumber];
    },
    player: function() {
      return this.xIsNext ? "X" : "O";
    }
  },
  methods: {
    onSquareSelection(event) {
      this.$set(this.current.squares, event.index, this.player);
      this.xIsNext = !this.xIsNext;
    }
  }
};
</script>