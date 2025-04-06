

<template>
  <div :style="{backgroundColor: bgColor}">
    <h2>Component Three</h2>
    <p>Choose background color</p>
    <input type="color" v-model="bgColor">
    <Strong>{{bgColor}}</Strong>
  </div>
</template>

<script>
export default {
  name: "CompThree",
  data() {
    return {
      bgColor: ''
    }
  }
}
</script>

<style scoped>

</style>