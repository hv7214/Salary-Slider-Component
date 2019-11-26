<template>
  <div id="switchbar">
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
      currency: "INR",
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
          width: 6
        },
        items: {
          delay: 0.35,
          preSelected: "INR",
          disabled: false,
          labels: [
            { name: "INR", color: "white", backgroundColor: "green" },
            { name: "USD", color: "black", backgroundColor: "gold" }
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
