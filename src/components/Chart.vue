<template>
  <div class="chart" :class="{ 'chart-dark': trackMode }">
    <km :trackMode="trackMode" :dreadmillMode="dreadmillMode"></km>
  </div>
</template>

<script>
import km from "./km.vue";
export default {
  name: "PaceChart",
  components: {
    km,
  },
  props: {
    trackMode: Boolean,
    dreadmillMode: Boolean,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.chart {
  background-color: #ffffff;
  height: 100%;
  transition: background-color 0.6s ease;
}
.chart-dark {
  background-color: #1a1a2e;
}
</style>
