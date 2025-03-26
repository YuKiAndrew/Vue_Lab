<template>
  <h1>Example: Range Watcher</h1>
  <p>A watcher is used for the 'rangeVal' value so that values between 20 and 60 are not possible to choose.</p>
  <div id="watcher">
    <input type="range" v-model="rangeVal" max="1" min="0" step="0.1">
    <p><code>{{ rangeVal }}</code></p>
  </div>
  <p>Mouse Pointer Position Change</p>
  <div id="findTheDifferential">
    <div v-on:click="getxPois"></div>
    <p>{{this.diff}}, {{this.ydiff}}</p>
  </div>
  <p>verify the email address</p>
  <div id="checkTheValidEmailAddress">
    <input type="email" v-model="ipAddress">
    <p v-bind:class="myClass">{{ feedbackText }}</p>
  </div>
</template>

<script >
export default {
  name: "watcherTest",
  props : {
    isShow: Boolean
  },
  watch: {
    rangeVal(val) {
      if (val > 0.5) {
        this.rangeVal = 0.5
      }
    },
    xpois(newVal, oldVal) {
      this.diff = newVal - oldVal
    },
    ypois(newVal, oldVal) {
      this.ydiff = newVal - oldVal
    },
    ipAddress(newVal,oldVal) {
      if (!newVal.includes('@')) {
        this.feedbackText = "this is not the valid email";
        this.myClass = "invalid"
      } else if(!oldVal.includes('@') && newVal.includes('@')) {
        this.feedbackText = "Perfect! You fixed it!"
        this.myClass = "valid"
      } else {
        this.feedbackText = "The email address is valid :)";
      }
    }
  },
  methods: {
    getxPois(event) {
      this.xpois = event.offsetX
      this.ypois = event.offsetY
    }
  },
  data () {
    return {
      rangeVal: 0,
      xpois: 0,
      diff: 0,
      ypois: 0,
      ydiff: 0,
      ipAddress: '',
      feedbackText: '',
      myClass: 'invalid'
    }
  }
}
</script>

<style scoped>
#findTheDifferential > div {
  width: 200px;
  height: 50px;
  border: solid black 1px;
  background-color: lightgreen;
}
#findTheDifferential {
  border: dashed black 1px;
  display: inline-block;
  padding: 10px;
}
.valid {
  color: green;
}
.invalid {
  color: red;
}
</style>