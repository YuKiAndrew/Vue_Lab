

<template>
  <div v-show="isFavorite">
    <h2>
      {{ foodName }}
    </h2>
    <p>{{ foodDesc }}</p>
  </div>
  <div id="changeProp">
    <p>{{foodIsFavorite}}</p>
    is it food your favorite?
    <br>
    <button @click="toggleFavorite">Favorite</button>
  </div>
</template>

<script>
export default {
  props: {
    foodName: {
      type: String,
      required: false,
      default: "juice"
    },
    foodDesc: {
      type: String,
      required: false,
      default: 'This is the default description',
      validator: function(value) {
        return 20 < value.length && value.length < 50;
      }
    },
    isFavorite: {
      type:Boolean,
      default: true
    }
  },
  watch: {
    foodDesc(newVal) {
      if (!this.validationFoodDesc(newVal)){
        this.validationError.foodDesc = 'Description must be between 20 and 50 characters.';
      } else {
        this.validationErrors.foodDesc = '';
      }
    }
  },
  mounted() {
    console.log(this.foodName)
  },
  methods: {
    validationFoodDesc(value) {
      return value.length >= 20 && value.length <= 50;
    },
    toggleFavorite() {
      this.foodIsFavorite = !this.foodIsFavorite
    }
  },
  data() {
    return {
      validationError : {},
      foodIsFavorite: this.isFavorite
    }
  }
}
</script>

<style scoped>

</style>