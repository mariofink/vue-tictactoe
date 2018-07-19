<template>
  <div>
    <h3>Moves</h3>
    <ul>
      <li v-for="(entry, index) in history" :key="index">
        <button @click="moveTo(index)" :class="{highlight: isCurrentStep(index)}">
          {{buttonCaption(index, entry)}}
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
    moveTo(index) {
      this.$emit("move", index);
    },
    buttonCaption: function(index, entry) {
      if (index === 0) {
        return `Go to game start`;
      }
      if (index > 0 && entry.position !== null) {
        return `Go to move #${index} 
        (Row: ${entry.position.row} Column: ${entry.position.col})`;
      }
    },
    isCurrentStep(index) {
      return index === this.currentStep;
    }
  }
};
</script>

<style scoped>
.highlight {
  font-weight: bold;
}
</style>

