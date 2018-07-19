<template>
  <div>
    <button class="square" @click="clickHandler"></button>
  </div>
</template>

<script>
export default {
  name: "square",
  props: ["index"],
  methods: {
    clickHandler() {
      this.$emit("selection", { index: this.index });
    }
  }
};
</script>