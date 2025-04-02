

<template>
  <h3>Todo List</h3>
  <ul>
    <todo-item
        v-for="x in items"
        :key="x"
        :item-name="x"
        style="background-color: lightgreen;"
    />
  </ul>
  <input placeholder="Add things to do here" v-model="newItem" v-on:keydown.enter="addItem">
  <button v-on:click="addItem">Add</button>
  <br>
</template>
<script>
import TodoItem from "@/components/TodoItem.vue";
export default {
  data() {
    return {
      newItem: '',
      items: ['Buy apples','Make pizza','Mow the lawn']
    }
  },
  methods: {
    addItem() {
      this.items.push(this.newItem)
      this.newItem = ''
    }
  },
  components: {
    TodoItem
  }
}
</script>
<style>
</style>