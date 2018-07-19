<template>
  <div>
    <h1>Tic Tac Toe</h1>
    <div class="game">
      <div class="game-board">
        <board :squares="current.squares" @squareSelection="onSquareSelection"></board>
      </div>
      <div class="game-info">
        <p>{{status}}</p>
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
      stepNumber: 0,
      status: ""
    };
  },
  computed: {
    current: function() {
      return this.history[this.stepNumber];
    },
    player: function() {
      return this.xIsNext ? "X" : "O";
    },
    winner: function() {
      return calculateWinner(this.current.squares);
    }
  },
  methods: {
    onSquareSelection(event) {
      if (this.winner) return;
      this.$set(this.current.squares, event.index, this.player);
      this.xIsNext = !this.xIsNext;
      this.updateStatus();
    },
    updateStatus() {
      if (this.winner) {
        this.status = `Player ${this.winner} won!`;
      } else {
        this.status = "Next player: " + this.player;
      }
    }
  },
  mounted: function() {
    this.updateStatus();
  },
  updated: function() {
    this.updateStatus();
  }
};

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6]
  ];
  for (let line of lines) {
    const [a, b, c] = line;
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
</script>