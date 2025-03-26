

<template>
  <h1>Example: Data Property 'true' or 'false'</h1>
  <p>This is a responsive form feature made with Vue that gives feedback 'true' or 'false' when the user checks the checkbox.</p>
  <div id="computedProperties">
    <form>
      <p>
        Important item?
        <label>
          <input type="checkbox" v-model="val"> {{isVal}}
        </label>
      </p>
    </form>
  </div>
</template>

<script >
export default {
  name: "computedProperties",
  props: {
    isShow: Boolean
  },
  data() {
    return {
      val: true,

    }
  },
  computed: {
    isVal() {
      if (this.val) {
        return "yes";
      } else {
        return "no";
      }
    }
  }
}

</script>

<style scoped>

</style>