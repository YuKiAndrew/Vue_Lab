<template>
  <div id="eventModifier" v-show="isShow">
    <div id="createAlert">
      <p>Create the button to create an alert</p>
      <button v-on:click.once="createAlert">Create Alert</button>
    </div>
    <div id="getKey">
      <input v-on:keydown="getKey" placeholder="getKey test">
      <p>{{getKeys}}</p>
    </div>
    <div id="longTimeKeyPress" class="fx">
      <div>
        <textarea rows="5" name="test-target" id="test-target" v-model="textArea" @keydown="handleKeyDown" @beforeinput="handleBeforeInput" @input="handleInput" @keyup="handleKeyUp"></textarea>
        <button type="button" name="btn-reset" id="btn-reset" @click="resetClick">resetButton</button>
      </div>
      <div id="flex">
        <pre id="console-log" v-html="consoleLog"></pre>
      </div>
    </div>
    <div id="specific keyboard test">
      <p> Try pressing the 's' key:</p>
      <textarea v-on:keydown.ctrl="createAlertForShift" placeholder="press ctrl to find something surprisingly"></textarea>
      <div>
        <textarea @keydown.ctrl.shift="createAlertForCtrlAndShift" placeholder="press ctrl and shift to find something surprisingly"></textarea>
      </div>
    </div>
    <div v-on:click.right.ctrl="changeColor" v-bind:style="{backgroundColor:'hsl('+bgColor+',80%,80%)'}">
      <p>Press right mouse button here.</p>
    </div>
    <div v-on:click.right.prevent="changeColorPrevent" v-bind:style="{backgroundColor:'hsl('+bgColorP+',80%,80%)'}">
      <p>Press right mouse button here.</p>
    </div>
  </div>
</template>

<script>

export default {
  name: "eventModifier",
  props: {
    isShow: Boolean
  },
  data() {
    return {
      getKeys: '',
      consoleLog: '',
      textArea: '',
      bgColor: 0,
      bgColorP: 0
    }
  },
  methods: {
    createAlert() {
      alert("Alert created from button click")
    },
    getKey(env) {
      this.getKeys = env.key
      console.log(this.getKeys)
    },
    logMessage(message) {
      this.consoleLog += message + "</br>"
    },
    handleKeyDown(event) {
      if (!event.repeat) {
        this.logMessage("press" + event.key + " trigger keydown")
      } else {
        this.logMessage("repeat press" + event.key + " trigger keydown")
      }
    },
    handleBeforeInput(event) {
      this.logMessage("it will input " + event.data + " trigger before input")
    },
    handleInput(event) {
      this.logMessage('enter '+ event.data +" trigger input event");
    },
    handleKeyUp(event) {
      this.logMessage("release " + event.key + "trigger keyup")
    },
    resetClick() {
      this.consoleLog =''
      this.textArea=''
    },
    createAlertForShift() {
      alert("You pressed the 'ctrl  ' key!")
    },
    createAlertForCtrlAndShift() {
      alert("You pressed the 'ctrl' and 'shift' key!")
    },
    changeColor() {
      this.bgColor += 50
    },
    //prevent drop down menu appear
    changeColorPrevent() {
      this.bgColorP += 50
    }

  }
}
</script>

<style>

</style>