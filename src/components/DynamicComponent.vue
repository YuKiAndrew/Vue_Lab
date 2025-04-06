

<template>
  <div id="SwitchComponent">
    <br/>
    <h1>Dynamic Component</h1>
    <p>App.vue switches between which component to show.</p>
    <button @click="toggleValue = !toggleValue">
      Switch Component
    </button>
    <!--    include means only compOne will keep alive.-->
    <!--    exclude means exclude compOne, other component will keep alive-->
    <KeepAlive include="CompOne">
      <component v-bind:is="activeComp"></component>
    </KeepAlive>
  </div>
</template>

<script>
import CompOne from "@/components/DynamicComponent/CompOne.vue";
import CompTwo from "@/components/DynamicComponent/CompTwo.vue"

export default {
  components: {
    CompOne,
    CompTwo
  },
  data() {
    return {
      toggleValue: true
    }
  },
  computed: {
    activeComp() {
      if(this.toggleValue) {
        return 'comp-one'
      } else {
        return 'comp-two'
      }
    }
  }
}

</script>

<style scoped>

</style>