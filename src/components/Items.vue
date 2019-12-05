<template>
  <div>
    <MainTitle :label="`Items (${itemsRemaining()})`" size="h2" />
    <ul>
      <li :key="item.id" v-for="(item, index) in items">
        <span
          @click="$emit('toggleItem', index)"
          :class="{completed: item.completed}"
        >{{ item.label }}</span>
        <button @click="$emit('deleteItem', index)">delete</button>
      </li>
    </ul>
    <p class="no-items" v-show="!items.length">No items, enjoy your day</p>
  </div>
</template>

<script>
import Title from './Title';

export default {
  name: 'Items',
  components: {
    MainTitle: Title,
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
    padding: 0 0 0 20px;
  }
  li {
    cursor: pointer;
    user-select: none;
  }
  span.completed {
    color: #AAA;
    text-decoration: line-through;
  }
  .no-items {
    color: darkgreen;
  }
</style>
