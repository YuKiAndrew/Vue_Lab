

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
      <div v-for="(item,index) in images" v-bind:key="item" id="bindclass">
        <img v-bind:src = "item.imageUrl" v-on:click="select(index)" v-bind:class="{selClass: item.sel}" alt="item.name">
      </div>
    </div>
    <div id="impClass" class="impClass" v-bind:class="{yelClass: isYellow}">
      This div belongs to both 'impClass' and 'yelClass'.
    </div>
    <div id="multipleClass" v-bind:class=" [{impClass: isMultiple}, 'yelClass']">
      Test Multiple Classes
    </div>
  </div>
</template>

<script>
import bg from "@/assets/img_notebook.png"
import breakfast from "@/assets/food collection/breakfast_img.png"
import drums from "@/assets/food collection/drumsticks.png"
import fastfood from "@/assets/food collection/fast_food.png"

export default {
  name: "vueCssB",
  props: {
    isShow: Boolean
  },
  methods: {
    select(num) {
      this.images[num].sel = !this.images[num].sel
    }
  },
  data() {
    return {
      opacity: 0.8,
      imageUrl: bg,
      images : [
        {name: "breakfast", price: 10, imageUrl: breakfast, sel: false},
        {name: "drumsticks", price :5, imageUrl: drums, sel: false},
        {name: "fast food", price :15, imageUrl: fastfood, sel: false}
      ],
      isYellow: true,
      isMultiple: true
    }
  },
  watch: {
    opacity(newValue) {
      console.log(`New opacity: ${newValue}`);
      console.log(`Background color: rgba(99, 0, 89, ${newValue})`);
    },

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
#selectImageWithVBindClass {
  display: flex;
}
#bindclass {
  box-sizing: border-box;
  width: 100%;
  padding: 3px;
  border: solid white 4px;
  border-radius: 5px;
  display: inline-block;
}
#bindclass > img {
  box-sizing: border-box;
  width: 50px;
  padding: 3px;
  border: solid white 4px;
  border-radius: 5px;
  display: inline-block;
}
img:hover {
  cursor: pointer;
}
.selClass {
  border: solid brown 4px;
  background-color: lightpink;
}
.impClass {
  font-weight: bolder;
}
.yelClass {
  background-color: rgb(255, 255, 136);
}
#impClass {
  border: dashed black 1px;
  width: 200px;
  margin: 20px;
  padding: 20px;
}
</style>