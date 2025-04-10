

<template>
  <h1>Example</h1>
  <p>Click the button to put 'Hello!' as the text in the green P element.</p>
  <button @click="changeVal">Change Text</button><br>
  <p ref="pEl" id="pEl">This is the initial text</p>
  <div id="copyFromOneTagToAnother">
    <h1>Copy Example</h1>
    <p ref="p1">Click the button to copy this text into the paragraph below.</p>
    <button type="button" @click="copyRefVal">Copy Val</button>
    <p ref="p2">empty</p>
  </div>
  <div id="obtainInputVal">
    <h1>Example for template input</h1>
    <input ref="input" placeholder="write something" @blur="storeInputVal">
    <p ref="p3">This is the p3 field</p>
  </div>
  <div id="refWithVFor">
    <h1>Example for v-for</h1>
    <button @click="getValue">Get the 3rd list element</button><br>
    <ul>
      <li v-for="x in liTexts" ref="liEl">{{x}}</li>
    </ul>
    <pre>{{thirdEl}}</pre>
  </div>
</template>

<script>
export default {
  methods: {
    changeVal() {
      this.$refs.pEl.innerHTML = "Hello!"
    },
    copyRefVal() {
      this.$refs.p2.innerHTML = this.$refs.p1.innerHTML
    },
    storeInputVal() {
      this.$refs.p3.innerHTML = this.$refs.input.value
    },
    getValue() {
      this.thirdEl = this.$refs.liEl[2].innerHTML
    }
  },
  data() {
    return {
      thirdEl: '',
      liTexts: ['Apple','Banana','Kiwi','Tomato','Lichi']
    }
  }
}
</script>

<style scoped>
#pEl {
  background-color: lightgreen;
  display: inline-block;
}
</style>