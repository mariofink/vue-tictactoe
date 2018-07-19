<template>
  <button class="square" @click="clickHandler">{{value}}</button>
</template>

<script>
export default {
  name: "square",
  props: ["index", "value"],
  methods: {
    clickHandler() {
      this.$emit("selection", { index: this.index });
    }
  }
};
</script>