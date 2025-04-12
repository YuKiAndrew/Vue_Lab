
<template>
  <div v-show="isShow">
    <div id="testBeforeCreate">
      <h3>beforeCreateTest</h3>
      <p id="beforeResult">{{texts}}</p>
    </div>
    <div id="testCreate">
      <h3>createTest</h3>
      <p id="createdResult">{{createdText}}</p>
    </div>
    <div id="mountedComponent">
      <h3>mounted component</h3>
      <p ref="pName">ref element</p>
    </div>
    <div id="beforeUpdate">
      <h3>beforeUpdate test</h3>
      <button @click="countIncrease">count + 1</button>
      <p ref="countRef">{{count}}</p>
      <ol ref="divLog"></ol>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      texts: '...',
      createdText: '...',
      count: 0
    }
  },
  props: {
    isShow: Boolean
  },
  beforeCreate() {
    this.texts = 'initial text';
    console.log("beforeCreate " + this.texts);
  },
  created() {
    this.createdText = 'created text'
    console.log("createdText" + this.createdText)
  },
  mounted() {
    alert("we will see that this alter will generate before rendering. Even though the DOM has been mounted, the alter function stop rendering process")
    this.$refs.pName.innerHTML = 'after mounted, the ref element can be altered.'
  },
  beforeUpdate() {
    this.$refs.countRef.innerHTML += 'after updated, the ref element can be altered.'
    console.log(this.$refs.countRef.innerHTML)
    //the new value of this.$refs.countRef.innerHTML will not be shown on the page because it is beforeupdate, the count number will soon overwrite it.
    this.$refs.divLog.innerHTML += "<li>beforeUpdate: This happened just before the 'updated' hook.</li>";
  },
  updated() {
    console.log("the component is updated")
  },
  methods: {
    countIncrease() {
      this.count += 1
    }
  }
}

</script>

<style>

</style>