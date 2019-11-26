<template>
  <div id="scale" v-bind:style="{ width: width + 'em' }">
    <div id="start">{{ minSalary }}</div>
    <div id="end">{{ maxSalary }}</div>
  </div>
</template>

<script>
export default {
  name: "Scale",
  props: {
    currency: {
      required: true,
      default: "Rupees",
      type: String
    }
  },
  data() {
    return {
      minSalary: "10",
      maxSalary: "1Cr",
      width: 27
    };
  },
  watch: {
    currency: function() {
      if (this.currency === "Rupees") {
        this.minSalary = "10";
        this.maxSalary = "1Cr";
      } else if (this.currency === "Dollars") {
        this.minSalary = "50000";
        this.maxSalary = "5000000";
      }
    }
  }
};
</script>

<style scoped>
#scale {
  display: flex;
  justify-content: space-between;
  margin-right: 100px;
}
</style>
