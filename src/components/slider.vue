<template>
  <div id="slider" v-bind:style="{ width: width + 'em' }">
    <vue-slider
      v-model="value"
      :dot-size="dotSize"
      :contained="true"
      :min="min"
      :max="max"
      :enable-cross="cross"
      :min-range="range"
    ></vue-slider>
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
      default: "INR"
    }
  },
  data: function() {
    return {
      min: 10,
      max: 100,
      value: [10, 100],
      dotSize: 16,
      width: 26,
      cross: false,
      range: 1
    };
  },
  watch: {
    value: function() {
      this.$emit("valuechange", this.value[0], this.value[1]);
    },
    currency: function() {
      var originalAmt1 = this.value[0];
      var originalAmt2 = this.value[1];
      var convertedAmt1, convertedAmt2;
      if (this.currency === "INR") {
        this.min = 10;
        this.max = 100;
        convertedAmt1 = this.convertToRupees(originalAmt1, true);
        convertedAmt2 = this.convertToRupees(originalAmt2, false);
      } else if (this.currency === "USD") {
        this.min = 50000;
        this.max = 5000000;
        convertedAmt1 = this.convertToDollars(originalAmt1);
        convertedAmt2 = this.convertToDollars(originalAmt2);
      }
      this.value = [convertedAmt1, convertedAmt2];
    }
  },
  methods: {
    convertToDollars(INR) {
      return (INR * 100000) / 71.69 > 5000000
        ? 5000000
        : (INR * 100000) / 71.69;
    },
    convertToRupees(USD, flag) {
      let max = 100;
      if (flag) max = 99;
      return (USD * 71.69) / 100000 > 100 ? max : (USD * 71.69) / 100000;
    }
  }
};
</script>

<style scoped>
#slider {
  margin-top: 50px;
  margin-right: 50px;
}
</style>
