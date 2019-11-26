<template>
  <div id="switch">
    <toggle-switch
      :options="myOptions"
      :disabled="false"
      @input="select"
      v-model="myOptions"
    />
  </div>
</template>

<script>
import ToggleSwitch from "vuejs-toggle-switch";
export default {
  name: "Toggle",
  components: { ToggleSwitch },
  data() {
    return {
      currency: "Rupees",
      myOptions: {
        layout: {
          color: "black",
          backgroundColor: "lightgray",
          selectedColor: "white",
          selectedBackgroundColor: "green",
          borderColor: "black",
          fontFamily: "Arial",
          fontWeight: "normal",
          fontWeightSelected: "bold",
          squareCorners: false,
          noBorder: false
        },
        size: {
          fontSize: 1,
          height: 2,
          padding: 0.5,
          width: 9.2
        },
        items: {
          delay: 0.35,
          preSelected: "Rupees",
          disabled: false,
          labels: [
            { name: "Rupees", color: "white", backgroundColor: "green" },
            { name: "Dollars", color: "black", backgroundColor: "gold" }
          ]
        }
      }
    };
  },
  methods: {
    select(newVal) {
      this.currency = newVal;
      this.$emit("currencyupdate", this.currency);
    }
  }
};
</script>
