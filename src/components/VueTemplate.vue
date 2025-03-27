

<template>
  <h1>'template' Example</h1>

  <p>All HTML code from inside the div tag with id="app" is moved inside the 'template' configuration option, in backtick quotes.</p>
  <div id="vTemp" v-show="isShow">
  </div>
</template>
<script>
export default {
  name:"vTemp",
  props: {
    isShow:Boolean
  },
  template:
    `<h1>{{ message }}</h1>\n    <p>This is a second line of HTML code, inside backtick quotes</p>`,
  data() {
    return {
      message: "Hi"
    }
  }

}
</script>
<style scoped>
#vueTemplate {
  display: inline-block;
  padding: 10px;
  font-size: x-large;
  background-color: lightgreen;
}
</style>