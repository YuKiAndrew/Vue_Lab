<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <div v-bind:class="vueClass"> This elements</div>
  <div :style = "{ fontSize: size + 'px' }">bind size test</div>
  <div v-bind:style="{ backgroundColor: 'hsl('+bgVal + ',80%,80%)' }">Notice the background color on this div tag.</div>
  <p v-if="typewritersInStock">v-if in stock</p>
  <p v-else :style="{ fontSize: size + 'px' }">not in stack</p>
  <p v-if="text.includes('pizza')">The text includes the word 'pizza'</p>
  <p v-else>the word 'pizza' is not found in the text</p>
  <div v-show="showDiv" :style="{ fontSize: size + 'px' }">This div tag can be hidden</div>
  <div v-show="showd">this is v-show</div>
  <div v-if="showd">this is v-if</div>
  <div>
      <p v-for="(x, index) in manyfoods" :key = "index">{{index}}: {{ x }}</p>
  </div>
  <div>
    <p v-for="(x,index) in manyfoodsv2" :key = index>
      {{index}}: "{{x}}", url: "{{x.url}}" <br>
    </p>
  </div>
  <div>
    <p> {{"count the number of clicks " + count}}</p>
    <button v-on:click="count++">Count</button>
  </div>
  <div>
    <p>{{"the total number of photos are " + methodCount}}</p>
    <button v-on:click = "countMethod"> countMethod</button>
  </div>
  <div v-on:mouseover="showd = !showd">
    <p> Mouse over me</p>
  </div>
  <div v-on:mouseleave="count++">
    <p>mosue leave me</p>
  </div>
  <div>
    <div v-show="lighton">
      <img src="/img.png">
    </div>
    <button v-on:click="lighton = !lighton">turn on light</button>
  </div>
  <div>
    <input v-on:input="inputCount++">
    <p>{{"input event occured:" +  inputCount}}</p>
  </div>

  <VonTest msg="VonTest file will conduct several experiments using v-on command"></VonTest>
  <Differet></Differet>
  <CountAnimals :isShow=false></CountAnimals>
  <EventModifier :isShow=false></EventModifier>
  <FormVue :isShow=false></FormVue>
  <VModelTest :isShow=false></VModelTest>
  <vue-css-b :is-show=true></vue-css-b>
  <vue-computed :is-show="true"></vue-computed>
  <vue-watch :is-show="true"></vue-watch>
  <vue-temp :is-show="true"></vue-temp>
  <h1>Props Test: Food</h1>
  <p>My favorite food has a diploma image attached to it.</p>
  <div id="wrapper">
    <vue-props-test
        food-name="Apples"
        food-desc="Apples are a type of fruit that grow on trees."
        v-bind:is-favorite="true"/>
    <vue-props-test
        food-name="Pizza"
        food-desc="Pizza has a bread base with tomato sauce, cheese, and toppings on top."
        v-bind:is-favorite="true"/>
    <input type="text" v-model="foodDes">
    <vue-props-test
        food-name="Rice"
        :food-desc= "foodDes"
        v-bind:is-favorite="true"/>
  </div>
  <v-for-vue></v-for-vue>
  <EmitCalculateMain :isShow="false"></EmitCalculateMain>
  <FallThroughAttri></FallThroughAttri>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import VonTest from './components/VonTest.vue'
import Differet from './components/Different.vue'
import CountAnimals from "@/components/CountAnimals.vue";
import EventModifier  from "@/components/EventModifier.vue";
import FormVue from "@/components/FormVue.vue";
import VModelTest from "@/components/VModelTest.vue"
import vueCssB from "@/components/VueCssBinding.vue"
import vueComputed from "@/components/ComputedProperties.vue"
import vueWatch from "@/components/WatcherTest.vue"
import vueTemp from "@/components/VueTemplate.vue"
import VuePropsTest from "@/components/VuePropsTest.vue"
import VForVue  from "@/components/VForVue.vue";
import EmitCalculateMain  from "@/components/EmitCalculateMain.vue";
import FallThroughAttri from "@/components/FallThroughAttri.vue";

export default {
  name: 'App',
  components: {
    HelloWorld,
    VonTest,
    Differet,
    CountAnimals,
    EventModifier,
    FormVue,
    VModelTest,
    vueCssB,
    vueComputed,
    vueWatch,
    vueTemp,
    VuePropsTest,
    VForVue,
    EmitCalculateMain,
    FallThroughAttri
  },
  data() {
    return {
      // message: 'Hello Vue.js!',
      vueClass: "pinkBG",
      size : 99,
      bgVal: 120,
      typewritersInStock: true,
      text: 'I like taco, pizza, Thai beef salad, pho soup and tagine.',
      showDiv: true,
      showd: true,
      manyfoods: ['pizza', 'tacos', 'burgers', 'pasta'],
      manyfoodsv2: [
        {name: 'Burrito', url: 'img_burrito.svg'},
        {name: 'Salad', url: 'img_salad.svg'},
        {name: 'Cake', url: 'img_cake.svg'},
        {name: 'Soup', url: 'img_soup.svg'},
        {name: 'Fish', url: 'img_fish.svg'},
        {name: 'Pizza', url: 'img_pizza.svg'},
        {name: 'Rice', url: 'img_rice.svg'}
      ],
      count: 0,
      methodCount: 0,
      lighton : false,
      inputCount: 0,
      foodDes: null
    }
  },
  methods: {
    countMethod() {
      this.methodCount += 9
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.writeText {
  width: 400px;
  height: 60px;
  background-color: lightgreen;
  padding: 20px;
  font-weight: bold;
  font-family: 'Courier New', Courier, monospace;
  text-align: center;
}
.textArea {
  width: 200px;
  height: 40px;
  background-color: coral;
  text-align: center;
  padding: 20px;
  font-weight: bolder;
}

</style>
