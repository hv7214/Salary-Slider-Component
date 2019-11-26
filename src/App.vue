<template>
  <div id="app">
    <div id="head">
      <div id="slider"><Slider :currency="currency" /></div>
      <div id="switch"><Toggle @currencyupdate="currencychange" /></div>
    </div>
    <Scale :currency="currency" />
  </div>
</template>

<script>
import Slider from "./components/slider";
import Toggle from "./components/switch";
import Scale from "./components/scale";

export default {
  name: "app",
  components: {
    Slider,
    Toggle,
    Scale
  },
  data() {
    return {
      min: 10,
      max: 100,
      currency: "INR"
    };
  },
  methods: {
    currencychange(newcurrency) {
      this.currency = newcurrency;
    }
  }
};
</script>

<style>
#app {
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
