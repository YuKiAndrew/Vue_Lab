<template>
  <div id="animalCount" v-show="isShow">
    <div id="moose">
      <button v-on:click="addAnimal($event, +1)">+1</button>
      <button v-on:click="addAnimal($event, +5)">+5</button>
      <button v-on:click="addAnimal($event, -1)">-1</button>
    </div>
    <div id="deer">
      <button v-on:click="addAnimal($event, +1)">+1</button>
      <button v-on:click="addAnimal($event, +5)">+5</button>
      <button v-on:click="addAnimal($event, -1)">-1</button>
    </div>
    <div id="owl">
      <button v-on:click="addAnimal($event, +1)">+1</button>
      <button v-on:click="addAnimal($event, +5)">+5</button>
      <button v-on:click="addAnimal($event, -1)">-1</button>
    </div>
    <ul>
      <li>Moose: {{mooseNum}}</li>
      <li>Deer: {{deerNum}}</li>
      <li>owl: {{owlNum}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "AnimalCount",
  props: {
    isShow: Boolean
  },
  data() {
    return {
      mooseNum: 0,
      deerNum: 0,
      owlNum: 0
    }
  },
  methods : {
    addAnimal(e, num) {
      if (e.target.parentElement.id === 'moose') {
        this.mooseNum += num
      } else if (e.target.parentElement.id === 'deer') {
        this.deerNum += num
      } else {
        this.owlNum += num
      }
    }
  }
}

</script>

<style>

</style>