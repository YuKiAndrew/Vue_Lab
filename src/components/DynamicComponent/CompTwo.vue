<script>
export default {
  name: "CompTwo",
  data() {
    return {
      msg: ''
    }
  }
}

</script>

<template>
  <div>
    <h2>Two!</h2>
    <p>This is component two.</p>
    <input type="text" placeholder="write something" v-model="msg">
    <p>Your Message:</p>
    <p><strong>{{msg}}</strong></p>
  </div>
</template>

<style scoped>
  div {
    background-color: lightpink;
  }
</style>