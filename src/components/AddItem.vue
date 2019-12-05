<template>
  <div>
    <Title label="Add a new item" size="h2" />
    <form @submit="handleSubmit">
      <div class="form-group">
        <input class="form-group__input" ref="input" type="text" />
        <Button label="Add Item" type="submit" />
      </div>
      <span class="danger" v-show="invalid">Please enter an item</span>
    </form>
  </div>
</template>

<script>
import Button from './Button';
import Title from './Title';

export default {
  name: 'AddItem',
  components: {
    Button,
    Title,
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
  .form-group {
    display: flex;
    justify-content: space-between;
  }
  .form-group__input {
    box-sizing: border-box;
    padding: 10px;
    width: calc(100% - 120px);
  }
  .danger {
    color: darkred;
    display: block;
    margin: 10px 0 0 0;
  }
</style>
