<template>
  <div class="chart">
    <km></km>
  </div>
</template>

<script>
import km from "./km.vue";
export default {
  name: "PaceChart",
  components: {
    km,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.chart {
  background-color: #ffffff;
  height: 100%;
}
</style>
