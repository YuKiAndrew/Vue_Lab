

<template>
  <div v-show="isShow">
  <div id="submitForm">
    <form v-on:submit.prevent="addItem">
      <p>Add Item</p>
      <p>Item name: <input type="text" required v-model="itemName"></p>
      <p>How many: <input type="number" v-model="itemNum"></p>
      <button type="submit">Add item</button>
    </form>
    <p>Shopping list: </p>
    <ul>
      <li v-for="item in shoppingList" v-bind:key=item>{{item.name}}, {{item.number}}</li>
    </ul>
  </div>
  </div>
</template>

<script>
export default {
  name: "formSubmit",
  data() {
    return {
      itemName: null,
      itemNum: null,
      shoppingList: [
        {name: 'Tomatoes', number: 5}
      ]
    }
  },
  props: {
    isShow: Boolean
  },
  methods: {
    addItem() {
      let item = {
        name: this.itemName,
        number: this.itemNum
      }
      this.shoppingList.push(item);
      console.log(item);
      this.itemName = null;
      this.itemNum = null;
    }
  }
}
</script>

<style scoped>

</style>