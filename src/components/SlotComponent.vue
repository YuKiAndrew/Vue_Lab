

<template>
  <div id="slots">
    <h3>Slots in Vue</h3>
    <p>We send 'Hello World!' as content to the slot tag inside the SlotComp.vue component from App.vue.</p>
    <vue-slot>Change our mind, find new world</vue-slot>
  </div>
  <div id="wrapper">
    <vue-slot v-for="x in foods" v-bind:key="x">
      <img v-bind:src="x.url" alt="x.name">
      <h4>{{x.name}}</h4>
      <p>{{x.desc}}</p>
    </vue-slot>
  </div>
  <div id="fallbackComponent">
    <vue-slot></vue-slot>
  </div>
  <div id="testVSlot">
    <h1>Test VSlot</h1>
    <p>The Component has two div tags with one slot in each.</p>
    <VSlot >
      <template v-slot:topSlot>
        'Hi!'
      </template>
    </VSlot>
  </div>
  <div id="defaultslot">
    <h4>Test default slot</h4>
    <p>There are default slot in here</p>
    <VSlot>
      <template v-slot:default>'This is default slot'</template>
    </VSlot>
  </div>
  <div id="templateSlot">
    <h4>Test template slot</h4>
    <VSlot>
      <template v-slot:bottomSlot>
        <h4>To the bottom slot!</h4>
        <p>This p tag and the h4 tag above are directed to the bottom slot with the v-slot directive used on the template tag.</p>
      </template>
        <p>This goes into the default slot</p>
    </VSlot>
  </div>
  <div id="shortHandForSlot">
    <VSlot>
      <template #default>
        'Hello with pun sign'
      </template>
    </VSlot>
  </div>
  <hr/>
  <div id="slotScope">
    <slot-scope v-slot="dataFromSlot">
      <h2>{{ dataFromSlot.lclData}}</h2>
    </slot-scope>
  </div>
  <div id="slotScopeWithVFor">
    <h1>Scoped Slot</h1>
    <p>App.vue controls how local data from the scoped slot is rendered.</p>
    <br>
    <slot-scope-t>
      <template v-slot:slotWithName="text">
        <p>{{text.dynamicText}}</p>
      </template>
    </slot-scope-t>
  </div>
  <footer>
    <vue-slot>
      <h4>Footer</h4>
    </vue-slot>
  </footer>
</template>

<script>

import VueSlot from "@/components/VueSlot.vue";
import breakfast from "@/assets/food collection/breakfast_img.png"
import drums from "@/assets/food collection/drumsticks.png"
import fast_food from "@/assets/food collection/fast_food.png"
import VSlot from "@/components/VSlot.vue";
import slotScope from "@/components/SlotScope.vue";
import slotScopeT from "@/components/SlotScopeT.vue";


export default {
  name: "SlotsComp",
  components: {
    VueSlot,
    VSlot,
    slotScope,
    slotScopeT

  },
  data() {
    return {
      foods: [
        {name: 'BreakFast', desc: 'BreakFast is a good way to help you strong', url:breakfast},
        {name: 'drumsticks', desc: 'Drumsticks is a good option for supper', url:drums},
        {name: 'fastfoods', desc: 'good way to finish the lunch', url:fast_food}
      ]
    }
  }
}
</script>

<style scoped>
p {
  width: 200px;
  display: inline-block;
}
#slots {
  border: dashed black 1px;
  margin: 10px;
  padding: 10px;
}

</style>