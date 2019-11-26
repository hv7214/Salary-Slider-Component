<template>
  <div id="salaryslider">
    <div id="head">
      <div id="slider">
        <Slider :currency="currency" @valuechange="updatePtr" />
      </div>
      <div id="switch">
        <Toggle @currencyupdate="currencychange" />
      </div>
    </div>
    <Scale :currency="currency" />
  </div>
</template>

<script>
import Slider from "./components/slider";
import Toggle from "./components/switch";
import Scale from "./components/scale";

export default {
  name: "SalarySlider",
  components: {
    Slider,
    Toggle,
    Scale
  },
  props: {
    leftptr: {
      type: Number,
      required: false,
      default: 10
    },
    rightptr: {
      type: Number,
      required: false,
      default: 100
    },
    currency: {
      type: String,
      required: false,
      default: "INR"
    }
  },
  methods: {
    currencychange(newcurrency) {
      this.currency = newcurrency;
      this.$emit("changecurrency", newcurrency);
    },
    updatePtr(lptr, rptr) {
      this.leftptr = lptr;
      this.rightptr = rptr;
      this.$emit("changeptr", lptr, rptr);
    }
  }
};
</script>

<style>
#salaryslider {
  width: 40em;
  position: relative;
}
#head {
  display: flex;
}
#switch {
  width: 20%;
  margin-top: 40px;
}
</style>
