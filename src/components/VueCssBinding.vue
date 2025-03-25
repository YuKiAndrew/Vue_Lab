

<template>
  <div id="vueCss" v-show="isShow">
    <div id="changeBackColor">
      <h1>Example: In-line styling</h1>
      <p>This is an example of in-line styling with Vue (v-bind:style).</p>
      <p></p>

      <input type="range" max="1" min="0" step="0.1" v-model="opacity">{{opacity}} (opacity value)
      <br>
      <div id="image" v-bind:style="{ backgroundColor: 'rgba(99,0,89,' + opacity + ')'}">
      <div id="onTop" ></div>
      </div>
    </div>
    <div id="selectImageWithVBindClass">
      <div v-for="item in images" v-bind:key="item">

      </div>
    </div>
  </div>
</template>

<script>
import bg from "@/assets/img_notebook.png"

export default {
  name: "vueCssB",
  props: {
    isShow: Boolean
  },
  methods: {
  },
  data() {
    return {
      opacity: 0.8,
      imageUrl: bg
    }
  },
  watch: {
    opacity(newValue) {
      console.log(`New opacity: ${newValue}`);
      console.log(`Background color: rgba(99, 0, 89, ${newValue})`);
    }
  }
}
</script>

<style scoped>
#image {
  position: relative;
  border: dashed black 1px;
  width: 200px;
  height: 100px;
  background-size: cover;
}
</style>