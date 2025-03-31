<script>
import VueEmit from "@/components/VueEmit.vue"

export default {
  name:"emitMain",
  props : {
    isShow: Boolean
  },
  components: {
    VueEmit
  },
  methods: {
    calM(n1,n2) {
      console.log("value of n1 " + n1)
      this.result = n1 + n2
    },
    findResult(b1) {
      console.log(b1)
      if (b1 === true) {
        alert("The item has been found.");
      } else {
        alert("The item still needs some time to be found.");
      }
    },
    handleBlur(e) {
      this.item=e.target.value
    }
  },
  data() {
    return {
      result: 0,
      n1 : 0,
      n2 : 0,
      item: ''
    }
  }
}
</script>

<template>
  <div id="emitCalcualte" v-show="isShow">
    <VueEmit v-on:calculate-result="calM" :result="result"></VueEmit>

  </div>
  <div id="findParticularItem">
    <h4>find item in the item list</h4>
    <input type="text" @blur="handleBlur">
    <br>{{item}}
    <VueEmit v-on:is-find="findResult" v-bind:itemHeri="item"></VueEmit>
  </div>

</template>

<style scoped>

</style>