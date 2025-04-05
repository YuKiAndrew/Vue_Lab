<script>
import breakfast from "@/assets/food collection/breakfast_img.png";
import drums from "@/assets/food collection/drumsticks.png";
import fast_food from "@/assets/food collection/fast_food.png";

export default {
  data() {
    return {
      foods: [
        {name: 'BreakFast', desc: 'BreakFast is a good way to help you strong', url:breakfast},
        {name: 'drumsticks', desc: 'Drumsticks is a good option for supper', url:drums},
        {name: 'fastfoods', desc: 'good way to finish the lunch', url:fast_food}
      ],
      text: 'This text is from the data property'
    }
  }
}
</script>

<template>
  <div id="ScopedSlotWithArray">
    <template v-for="x in foods" :key="x">
      <slot :foodName="x.name" :foodDesc="x.desc" :foodUrl="x.url">
      </slot>
    </template>
  </div>
  <div id="ScopedSlot">
    <slot name="slotWithName" staticText="Static Text" :dynamicText="text">

    </slot>
  </div>
</template>

<style>

</style>