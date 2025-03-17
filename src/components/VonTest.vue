
<template>
  <div id="vonmouseover">
    <div v-on:mouseover="mouseover = !mouseover">mouseover</div>
    <div v-show="mouseover">mouseover test</div>
    <p> click on the box below:</p>
    <div class="writeText" v-on:click="writeText">{{text}}</div>
    <div v-on:mousemove="mousepos">
      <span>xPos: {{xPos}}</span> <br> <span>yPos: {{yPos}}</span>
    </div>
    <div id="textAreaId">
      <textarea class="textArea" v-on:input="writeTextArea" placeholder="start writing"></textarea>
      <span id="span"> {{ textArea }}</span>
    </div>
    <div>
      <p>put the number of moose in the input text:</p>
      <input type="number" v-on:input="seeMoose">
      <p>the number of moose: {{mooseNum}}</p>
    </div> <br>
    <div id="buttonList">
      <button v-on:click="addMoose($event,+1)">+1</button>
      <button v-on:click="addMoose($event,+5)">+5</button>
      <button v-on:click="addMoose($event,-1)">-1</button>
    </div>
    <div id="trigger id">
      <button v-on:click="messageMethod($event, 'hello')">event test</button>
      <p>Here is the message sent with the method, and the id of the img tag:</p>
      <p> {{message}}</p>
    </div>
  </div>
</template>

<style scoped>
#textAreaId {
  width: 100%;
  position: relative;
  margin-top: 10px;
  aspect-ratio: 1;
  background-image: url('@/assets/img_notebook.png');
  background-size: 340%;
  background-position: -345px 0;
  overflow: hidden;
  width: 800px;
  height: 400px;
}
#span {
  width: 200px;
  height: 100px;
  background-color: lightgreen;
}

</style>

<script>
export default {
  name: "VonTest",
  props: {
    msg: String
  },
  data() {
    return {
      mouseover: false,
      text: '',
      xPos: 0,
      yPos: 0,
      textArea: '',
      mooseNum: 0,
      message: "init"
    }
  },
  methods: {
    writeText() {
      this.text = "click the text"
    },
    mousepos(event) {
      this.xPos = event.offsetX
      this.yPos = event.offsetY
    },
    writeTextArea(event) {
      this.textArea = event.target.value
    },
    seeMoose(event) {
      const num = parseInt(event.target.value)
      if (!isNaN(num)) {
        this.mooseNum = num + this.mooseNum
      }
    },
    addMoose(event,num) {
      console.log("event:",event)
      if (!isNaN(num)) {
        this.mooseNum = num + this.mooseNum
      }
    },
    messageMethod(e,message) {
      this.message = this.message + ',' + message
    }
  }
}
</script>