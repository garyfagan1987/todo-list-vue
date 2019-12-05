<template>
  <button>{{ label }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    label: {
      required: true,
      type: String,
    },
  },
};
</script>

<style scoped>
  button {
    background-color: transparent;
    border: 1px solid #333;
    color: #333;
    cursor: pointer;
    padding: 10px;
    width: 100px;
  }
</style>