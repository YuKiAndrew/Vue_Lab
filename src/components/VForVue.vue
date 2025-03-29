

<template>
  <h1>Food</h1>
  <p>Components created with v-for based on an array</p>
  <div id="wrapper">
    <VuePropsTest v-for="item in foods" v-bind:key="item" v-bind:foodName="item">

    </VuePropsTest>
  </div>
  <div id = "secondQ">
    <VuePropsTest v-for="item in foodsWithDes" v-bind:key="item" v-bind:foodName="item.name" v-bind:food-desc="item.desc" v-bind:isFavorite="item.favorite">
    </VuePropsTest>
  </div>
</template>

<script>
import VuePropsTest from "@/components/VuePropsTest.vue";
export default {
  name: "VueComponent",
  components: {
    VuePropsTest
  },
  data() {
    return {
      foods: ['Apple', 'Pizza', 'Rice', 'Fish', 'Cake'],
      foodsWithDes: [
        { name: 'Apples',
          desc: 'Apples are a type of fruit that grow on trees.',
          favorite: true },
        { name: 'Pizza',
          desc: 'Pizza has a bread base with tomato sauce, cheese, and toppings on top.',
          favorite: true },
        { name: 'Rice',
          desc: 'Rice is a type of grain that people like to eat.',
          favorite: true },
        { name: 'Fish',
          desc: 'Fish is an animal that lives in water.',
          favorite: true },
        { name: 'Cake',
          desc: 'Cake is something sweet that tastes good.',
          favorite: true }
      ]
    }
  }
}
</script>

<style scoped>

</style>