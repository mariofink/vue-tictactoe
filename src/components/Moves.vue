<template>
  <div>
    <h3>Moves</h3>
    <ul>
      <li v-for="(entry, index) in history" :key="index">
        <button @click="moveTo(index)">Go to move #{{index}}</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "moves",
  props: ["history"],
  methods: {
    moveTo(index) {
      this.$emit("move", index);
    }
  }
};
</script>

