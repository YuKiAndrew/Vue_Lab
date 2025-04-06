

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
  <div id="SwitchThreeComponent">
    <br/>
    <h1>Switch Three Components</h1>
    <button @click="compNbr++">Next Component</button>
    <KeepAlive include="CompOne,CompThree">
      <component :is="activeThreeComp"></component>
    </KeepAlive>
  </div>
  <div id="RememberTheLastTwo">
    <p>With &lt;KeepAlive :max="2"&gt; only the last two visited components will remember the user input.</p>
    <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-one'"> One</label>
    <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-two'"> Two</label>
    <label><input type="radio" name="rbgComp" v-model="compName" :value="'comp-three'"> Three</label>
    <KeepAlive :max="2">
      <component :is="compName"></component>
    </KeepAlive>
  </div>
</template>

<script>
import CompOne from "@/components/DynamicComponent/CompOne.vue";
import CompTwo from "@/components/DynamicComponent/CompTwo.vue"
import CompThree from "@/components/DynamicComponent/CompThree.vue";

export default {
  components: {
    CompOne,
    CompTwo,
    CompThree
  },
  data() {
    return {
      toggleValue: true,
      compNbr: 1,
      compName: 'comp-one'
    }
  },
  watch : {
    compNbr(val) {
      if (val > 3) {
        this.compNbr = 1;
      }
    }
  },
  computed: {
    activeComp() {
      if(this.toggleValue) {
        return 'comp-one';
      } else {
        return 'comp-two';
      }
    },
    activeThreeComp() {
      if (this.compNbr === 1) {
        return 'comp-one';
      } else if (this.compNbr === 2) {
        return 'comp-two';
      } else {
        return 'comp-three';
      }
    }
  }
}

</script>

<style scoped>

</style>