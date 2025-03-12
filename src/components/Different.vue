

<template>
  <input type="text" v-bind:value="vbind"><br>
  v-bind value:<input type="text" :value="vbind">
  <p>{{vbind}}</p>
  <input type="text" v-model="vmodel"><br>
  v-model value:<input type="text" v-model="vmodel">
  <p>{{vmodel}}</p>
  <button v-on:click="von">click button</button><br>
  <button @click="von">click button {{on}} times </button>
</template>

<script>

export default {
  name: "biasBetweenCommands",
  data() {
    return {
      vbind: "vbind value",
      vmodel: "vmodel value",
      on: 0
    }
  },
  methods: {
    von() {
      this.on++;
    }
  }
}
</script>
<style>

</style>