<template>
  <h1 :class="size">{{ label }}</h1>
</template>

<script>
const sizes = ['h1', 'h2'];

export default {
  name: 'Title',
  props: {
    label: {
      required: true,
      type: String,
    },
    size: {
      default: 'h1',
      type: String,
      validator: prop => sizes.includes(prop),
    },
  },
};
</script>

<style scoped>
  .h1, .h2 {
    color: #333;
  }
  .h1 {
    font-size: 36px;
  }
  .h2 {
    font-size: 20px;
  }
</style>