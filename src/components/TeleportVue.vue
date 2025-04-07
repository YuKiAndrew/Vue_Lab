

<template>
  <div id="Teleport">
    <h1>Teleport</h1>
    <p> we move the red  from inside the component to the body tag.</p>
    <tele-one></tele-one>
  </div>
  <div id="TeleportTwo">
    <h1>Teleport Two</h1>
    <tele-two></tele-two>
  </div>
</template>

<script>
import teleOne from '@/components/DynamicComponent/TeleOne.vue'
import teleTwo from '@/components/DynamicComponent/TeleTwo.vue'

export default {
  name: "teleport",
  components: {
    teleOne,
    teleTwo
  }
}
</script>

<style>

</style>