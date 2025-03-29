

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
  <div id="addItem3">
    <form v-on:submit.prevent="addItemPrevent">
      <p>Add Item</p>
      <p>Item name: <input type="text" required v-model="itemNameText"></p>
      <p>How many: <input type="number" v-model="itemNumber"></p>
      <p>
        Important?
        <label>
          <input type="checkbox" v-model="itemImportant">
          {{ important }}
        </label>
      </p>
      <button type="submit">Add item</button>
    </form>
    <br>
    <hr>
    <div>
      <p><strong>Shopping list:</strong></p>
      <ul id="ulToFind">
        <li
            v-for="item in shoppingList"
            v-bind:class="{ impClass: item.important }"
            v-on:click="item.found=!item.found"
            v-show="!item.found"
            v-bind:key="item">
          {{item.name}},{{item.number}}
        </li>
      </ul>
      <ul id="ulFound">
        <li
          v-for="item in shoppingList"
          v-bind:class="{ impClass: item.important }"
          v-on:click="item.found=!item.found"
          v-show="item.found"
          v-bind:key="item">
          {{item.name}}, {{item.number}}
        </li>
      </ul>
    </div>
  </div>
  <div id="menuItem">
    <form v-on:submit.prevent="addOrder">
      <p><strong>Please Choose the food you would like to order</strong></p>
      <input type="radio" id="drink" required value="drink" v-model="orderThing">
      <label for="drink">
      drink</label>
      <label for="food">
      <input type="radio" id="food" required value="food" v-model="orderThing">
      food</label>
      <label for="dessert">
      <input type="radio" id="dessert" required value="dessert" v-model="orderThing">
      dessert</label>
      <br>
      <p v-show="orderThing">
      <label>
        <select required v-model="itemName" v-on:change="newUrl">
          <option value="" selected disabled>Select Item</option>
          <option v-for="item in preDefItems" v-bind:value="item.name" v-show="item.type === orderThing" v-bind:data-url="item.imgUrl" v-bind:key="item">
            {{item.name}}
          </option>
        </select>
      </label>
      </p>
      <img v-bind:src="itemUrl" alt="item Url">
      <p v-show="itemName">
        <input type="number" placeholder="How many?" v-model="itemN" required>
      </p>
      <button type="submit">Order</button>
    </form>
    <br>
    <hr>
    <div>
      <ul id="ulToFind">
        <li v-for="item in order" v-bind:key="item">
          {{item.name}}, {{item.number}} <img v-bind:src="item.url" alt="item url">
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import burritoImg from '@/assets/img_burrito.png';
import pizzaImg from '@/assets/img_pizza.png';

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
    },
    addItemPrevent(){
      let item = {
        name: this.itemName,
        number: this.itemNumber,
        important: this.itemImportant,
        found: false
      }
      this.shoppingList.push(item)
      this.itemName = null
      this.itemNumber = null
      this.itemImportant = false
    },
    addOrder() {
      let item ={
        name: this.itemName,
        number: this.itemN,
        url: this.itemUrl
      }
      this.order.push(item)
      this.orderThing = ""
      this.itemName = ""
      this.itemN = null
      this.itemUrl = null
    },
    newUrl(e) {
      this.itemUrl=e.target.options[e.target.selectedIndex].getAttribute("data-url")
    }
  },
  data() {
    return {
      inpText: "initial text",
      itemName: null,
      itemNum: null,
      itemImportant: false,
      shoppingList:[
        {name: 'tomato', number:5, important:false},
        { name: 'Bread', number: 1, important: false, found: false },
        { name: 'Soap', number: 1, important: true, found: true }
      ],
      orderThing: null,
      foodList: [],
      drinkList: [],
      dessertList: [],
      itemNameText: null,
      itemNumber: null,
      important: false,
      preDefItems: [
        { name: 'Burrito', type: 'food', imgUrl: burritoImg },
        { name: 'Pizza', type: 'food', imgUrl: pizzaImg },
        { name: 'Pho Soup', type: 'food', imgUrl: 'img_soup.svg' },
        { name: 'Spaghetti', type: 'food', imgUrl: 'img_spaghetti.svg' },
        { name: 'Fish', type: 'food', imgUrl: 'img_fish.svg' },
        { name: 'Cake', type: 'dessert', imgUrl: 'img_cake.svg' },
        { name: 'Rice', type: 'food', imgUrl: 'img_rice.svg' },
        { name: 'Salad', type: 'food', imgUrl: 'img_salad.svg' },
        { name: 'Coke', type: 'drink', imgUrl: 'img_soda.svg' },
        { name: 'Green Soda', type: 'drink', imgUrl: 'img_greenSoda.svg' },
        { name: 'Doughnut', type: 'dessert', imgUrl: 'img_doughnut.svg' },
        { name: 'Ice Cream', type: 'dessert', imgUrl: 'img_iceCream.svg' },
        { name: 'Lemonade', type: 'drink', imgUrl: 'img_lemonade.svg' },
        { name: 'Pancakes', type: 'dessert', imgUrl: 'img_pancakes.svg' },
        { name: 'Water', type: 'drink', imgUrl: 'img_water.svg' }
      ],
      order:[],
      itemN:'',
      itemUrl: null
    }
  }
}
</script>

<style scoped>
#addItem3 label:hover, #addItem3 li:hover {
  cursor: pointer;
  background-color: lightgray;
}
#addItem3 label, #addItem3 li {
  padding: 5px;
  border-radius: 5px;
}
ul {
  list-style-type: none;
}
li {
  margin: 2px;
  background-color: rgb(211, 254, 211);
}
.impClass {
  background-color: rgb(255, 202, 202);
}
#ulFound li {
  text-decoration: line-through;
  background-color: rgb(230,230,230);
}

</style>