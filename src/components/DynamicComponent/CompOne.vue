
<template>
  <div>
    <h2>One!</h2>

    <p>This is component one.</p>
    <p>Please choose food.
      <img :src="imgSrc" alt="select food" />
    </p>

    <label>
      <input type="radio" name="foodC" v-model="imgSrc" :value="require('@/assets/apple.png')">Apple
    </label>
    <label>
      <input type="radio" name="foodC" v-model="imgSrc" :value="require('@/assets/cake.png')">Cake
    </label>
  </div>
</template>

<script>
export default {
  name: "CompOne",
  data() {
    return {
      imgSrc: require('@/assets/question_mark.png')
    }
  }
}

</script>


<style scoped>
  div {
    background-color: lightgreen;
    height: 200px;
    align-items: center;
  }
  img {
    height: 40px;
    margin-top: 0px;
  }
  label:hover {
    cursor: pointer;
  }
</style>