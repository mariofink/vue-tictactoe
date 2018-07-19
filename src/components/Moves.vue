<template>
  <div>
    <h3>Moves</h3>
    <ul>
      <li v-for="(entry, move) in history" :key="move">
        <button @click="moveTo(move)" :class="{highlight: isCurrentStep(move)}">
          {{buttonCaption(move, entry)}}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "moves",
  props: ["history", "currentStep"],
  methods: {
    moveTo(move) {
      this.$emit("move", move);
    },
    buttonCaption: function(move, entry) {
      if (move === 0) {
        return `Go to game start`;
      }
      if (move > 0 && entry.position !== null) {
        return `Go to move #${move} 
        (Row: ${entry.position.row} Column: ${entry.position.col})`;
      }
    },
    isCurrentStep(move) {
      return move === this.currentStep;
    }
  }
};
</script>

<style scoped>
.highlight {
  font-weight: bold;
}
</style>

