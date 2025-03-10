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

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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
      lighton : false
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
</style>
