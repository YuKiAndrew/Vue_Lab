<template>
  <slot v-bind:lclData="data"></slot>
  <div id="slotWithVFor">
    <slot v-for="x in foods"
      :key="x"
      :foodName="x.name"
      :desc="x.desc"
      :foodUrl="x.url"></slot>
  </div>
</template>

<script>
import breakfast from "@/assets/food collection/breakfast_img.png";
import drums from "@/assets/food collection/drumsticks.png";
import fast_food from "@/assets/food collection/fast_food.png";

export default {
  name: "slotScope",
  data() {
    return {
      data: 'This is local data',
      foods: [
        {name: 'BreakFast', desc: 'BreakFast is a good way to help you strong', url:breakfast},
        {name: 'drumsticks', desc: 'Drumsticks is a good option for supper', url:drums},
        {name: 'fastfoods', desc: 'good way to finish the lunch', url:fast_food}
      ]
    }
  }
}

</script>

<style>

</style>