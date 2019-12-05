<template>
  <div>
    <MainTitle label="Todo List" />
    <AddItem v-on:submitItem="submitItem($event)" />
    <Items
      :items="items"
      v-on:deleteItem="deleteItem($event)"
      v-on:toggleItem="toggleItem($event)"
    />
  </div>
</template>

<script>
import uuid from 'uuid/v1';

import AddItem from '../components/AddItem';
import Items from '../components/Items';
import Title from '../components/Title';

export default {
  name: 'Index',
  components: {
    AddItem,
    Items,
    MainTitle: Title,
  },
  data() {
    return {
      items: [],
    };
  },
  methods: {
    deleteItem(index) {
      this.items.splice(index, 1);
    },
    toggleItem(index) {
      this.items[index].completed = !this.items[index].completed;
      localStorage.setItem('todos', JSON.stringify(this.items));
    },
    submitItem(label) {
      this.items.push({
        id: uuid(),
        label,
        completed: false,
      });
    },
  },
  created() {
    const data = localStorage.getItem('todos');
    this.items = data ? JSON.parse(data) : [];
  },
  updated() {
    localStorage.setItem('todos', JSON.stringify(this.items));
  },
};
</script>

<style>
  body {
    border: 1px solid #333;
    margin: 20px auto;
    padding: 0 20px;
    width: 360px;
  }
</style>