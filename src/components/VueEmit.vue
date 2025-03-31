

<template>
  <div id="VueEmit">
    <form id="formA" onsubmit="return false">
      <input type="number" placeholder="please type in multiplier1" v-model="m1">
      <input type="number" placeholder="please file in multiplier2" v-model="m2">
      <button type="submit" @click="emitMethod">submit</button>
    </form>
    <p>the result is : {{this.result}}</p>
  </div>
  <div id="findRes">

  </div>
</template>

<script>
export default {
  name:"VueEmitMethod",
  props: {
    result: Number,
    itemHeri: String
  },
  methods: {
    emitMethod() {
      this.$emit('calculate-result', this.m1, this.m2)
    }
  },
  watch: {
    m1(val) {
      console.log(val)
    },
    itemHeri(val) {
      console.log(val)
      let foundfood = this.itemList.some(item => item === val)
      console.log("what is the value of find method " + foundfood)
      this.$emit('is-find', foundfood)
    }
  },
  emits: ['is-find','calculate-result'],
  data() {
    return {
      m1: 0,
      m2: 0,
      itemList: ['apple','juice','pear','strawberry']
    }
  }
}
</script>

<style scoped>

</style>