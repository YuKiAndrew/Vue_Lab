<script>
export default {
  props: ['itemName']
};
</script>

<template>
  <li style="margin: 5px 0;" v-bind="$attrs">{{ itemName }}</li>
  <div class="pink"></div>
</template>

<style scoped>
li {
  margin: 0;
  border-radius: 10px;
  padding: 5px 10px;
}
.pink {
  display: inline-block;
  background-color: lightpink;
  padding: 5px;
  margin: 2px;
  border-radius: 50%;
}
</style>