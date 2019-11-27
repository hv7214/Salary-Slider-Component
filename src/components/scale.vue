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
      minSalary: "10 lakh",
      maxSalary: "1 Cr",
      width: 66
    };
  },
  watch: {
    currency: function() {
      if (this.currency === "INR") {
        this.minSalary = "10 lakh";
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
  font-size: 1em;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  margin-right: 100px;
}

#start,
#end {
  background-color: rgb(238, 255, 249);
}
</style>
