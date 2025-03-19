

<template>
  <div id="vModelTest" v-show="isShow">
    <input type="text" v-model="inpText">
    <p>{{inpText}}</p>
  </div>
  <div id="addItem">
    <form v-on:submit="addItem" id="addItemForm" onsubmit="return false;">
      <p>Add Item</p>
      <p>Item name: <input type="text" required v-model="itemName"></p>
      <p>How many: <input type="number" v-model="itemNum"></p>
      <p>
        Important?
        <label>
          <input type="checkbox" v-model="itemImportant">
          {{itemImportant}}
        </label>
      </p>
      <button type="submit">Add Item</button>
    </form>
    <hr>
    <p>Shopping List:</p>
    <ul>
      <li v-for="item in shoppingList" v-bind:key="item">{{item.name}}, {{item.number}}</li>
    </ul>
  </div>
</template>

<script>


export default {
  name:"vModelTest",
  components: {},
  props: {
    isShow: Boolean
  },
  methods: {
    addItem() {
      let item = {
        name: this.itemName,
        number: this.itemNum,
        important: this.itemImportant
      }
      this.shoppingList.push(item)
      this.itemName = null
      this.itemNum = null
      this.itemImportant = false
    }
  },
  data() {
    return {
      inpText: "initial text",
      itemName: null,
      itemNum: null,
      itemImportant: false,
      shoppingList:[
        {name: 'tomato', number:5, important:false}
      ]
    }
  }
}
</script>

<style scoped>

</style>