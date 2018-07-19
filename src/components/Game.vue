<template>
  <div>
    <h1>Tic Tac Toe (Vue.js)</h1>
    <div class="game">
      <div class="game-board">
        <board :squares="current.squares" @squareSelection="onSquareSelection"></board>
      </div>
      <div class="game-info">
        <div>{{status}}</div>
        <moves :history="history" :currentStep="stepNumber" @move="(index) => moveTo(index)"></moves>
      </div>
    </div>
  </div>
</template>

<script>
import Board from "./Board.vue";
import Moves from "./Moves.vue";

export default {
  name: "game",
  components: {
    Board,
    Moves
  },
  data: () => {
    return {
      history: [
        {
          squares: Array(9).fill(null),
          position: null
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
      this.history = this.history.slice(0, this.stepNumber + 1);
      const squares = this.current.squares.slice(
        0,
        this.current.squares.length
      );
      // do nothing if game already ended, or the square is already taken
      if (this.winner || squares[event.index]) return;
      squares[event.index] = this.player;
      this.history.push({
        squares: squares,
        position: getPosition(parseInt(event.index, 10))
      });
      this.stepNumber = this.history.length - 1;
      this.xIsNext = !this.xIsNext;
      this.updateStatus();
    },
    updateStatus() {
      if (this.winner) {
        this.status = `Player ${this.winner} won!`;
      } else {
        this.status = "Next player: " + this.player;
      }
    },
    moveTo(step) {
      this.stepNumber = step;
      this.xIsNext = step % 2 === 0;
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

/**
 * Get column and row number of a square index
 * @param {*} i
 */
function getPosition(i) {
  let row, col;
  if (i > 5) {
    row = 3;
    col = i - 5;
  } else if (i > 2) {
    row = 2;
    col = i - 2;
  } else {
    row = 1;
    col = i + 1;
  }
  return {
    row,
    col
  };
}
</script>