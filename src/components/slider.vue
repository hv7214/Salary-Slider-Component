<template>
  <div class="slider" v-bind:style="{ width: width + 'em' }">
    <div id="vs">
      <vue-slider
        v-model="value"
        :dot-size="dotSize"
        :contained="true"
        :min="min"
        :max="max"
      ></vue-slider>
    </div>
  </div>
</template>

<script>
import VueSlider from "vue-slider-component";
import "vue-slider-component/theme/material.css";
export default {
  name: "Slider",
  components: {
    VueSlider
  },
  props: {
    currency: {
      type: String,
      required: false,
      default: "Rupees"
    }
  },
  data: function() {
    return {
      min: 10,
      max: 100,
      value: [10, 100],
      dotSize: 15,
      width: 30
    };
  },
  watch: {
    currency: function() {
      var originalAmt1 = this.value[0];
      var originalAmt2 = this.value[1];
      var convertedAmt1, convertedAmt2;
      if (this.currency == "Rupees") {
        this.min = 10;
        this.max = 100;
        convertedAmt1 = this.convertToRupees(originalAmt1);
        convertedAmt2 = this.convertToRupees(originalAmt2);
      } else if (this.currency === "Dollars") {
        this.min = 50000;
        this.max = 5000000;
        convertedAmt1 = this.convertToDollars(originalAmt1);
        convertedAmt2 = this.convertToDollars(originalAmt2);
      }
      this.value = [convertedAmt1, convertedAmt2];
    }
  },
  methods: {
    convertToDollars(rupees) {
      return (rupees * 100000) / 71.69 > 5000000
        ? 5000000
        : (rupees * 100000) / 71.69;
    },
    convertToRupees(dollars) {
      return (dollars * 71.69) / 100000 > 100
        ? 100
        : (dollars * 71.69) / 100000;
    }
  }
};
</script>

<style scoped>
#vs {
  margin-top: 50px;
  margin-right: 50px;
}
</style>
