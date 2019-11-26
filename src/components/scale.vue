<template>
  <div id="scale" v-bind:style="{ width: width + '%' }">
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
      default: "INR",
      type: String
    }
  },
  data() {
    return {
      minSalary: "10",
      maxSalary: "1 Cr",
      width: 66
    };
  },
  watch: {
    currency: function() {
      if (this.currency === "INR") {
        this.minSalary = "10";
        this.maxSalary = "1 Cr";
      } else if (this.currency === "USD") {
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
