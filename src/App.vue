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
      currency: "rupees"
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
  width: 50em;
  position: relative;
}
#head {
  display: flex;
}
#switch {
  margin-top: 22px;
}
</style>
