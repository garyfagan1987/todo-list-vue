<template>
  <div>
    <Title :label="`Items (${itemsRemaining()})`" size="h2" />
    <ul>
      <li :class="{completed: item.completed}" :key="item.id" v-for="(item, index) in items">
        <div>
          <input @click="$emit('toggleItem', index)" type="checkbox" />
          <span @click="$emit('toggleItem', index)">{{ item.label }}</span>
        </div>
        <Button @click.native="$emit('deleteItem', index)" label="Delete" />
      </li>
    </ul>
    <p class="no-items" v-show="!items.length">No items, enjoy your day</p>
  </div>
</template>

<script>
import Button from './Button';
import Title from './Title';

export default {
  name: 'Items',
  components: {
    Button,
    Title,
  },
  props: {
    items: {
      type: Array,
      requried: true,
    },
  },
  methods: {
    itemsRemaining() {
      const count = this.items.reduce((n, item) => n + (item.completed === false), 0);
      return count;
    },
  },
};
</script>

<style scoped>
  ul {
    padding: 0;
  }
  input[type="checkbox"], span {
    cursor: pointer;
  }
  li {
    align-items: center;
    border-bottom: 1px solid #CCC;
    display: flex;
    justify-content: space-between;
    opacity: 1;
    padding: 10px 0;
    user-select: none;
    transition: all 250ms;
  }
  li:first-child {
    border-top: 1px solid #CCC;
  }
  .completed {
    opacity: 0.5;
  }
  .completed span {
    text-decoration: line-through;
  }
  .no-items {
    color: darkgreen;
  }
</style>
