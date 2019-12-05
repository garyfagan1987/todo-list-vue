<template>
  <div>
    <MainTitle label="Add a new item" size="h2" />
    <form @submit="handleSubmit">
      <input ref="input" type="text" />
      <button type="submit">Add Item</button>
      <span class="invalid" v-show="invalid">Please enter an item</span>
    </form>
  </div>
</template>

<script>
import Title from './Title';

export default {
  name: 'AddItem',
  components: {
    MainTitle: Title,
  },
  data() {
    return {
      invalid: false,
    };
  },
  methods: {
    handleSubmit() {
      if (this.$refs.input.value) {
        this.invalid = false;
        this.$emit('submitItem', this.$refs.input.value);
      } else {
        this.invalid = true;
      }
      this.$refs.input.value = '';
    },
  },
};
</script>

<style scoped>
  .invalid {
    color: darkred;
    display: block;
    margin: 10px 0 0 0;
  }
</style>
