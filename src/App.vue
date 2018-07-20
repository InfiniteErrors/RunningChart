<template>
<div class="wrapper">
  <header>
    <h1>RunningPace<span class="skinny">Chart</span></h1>
  </header>
    <Chart></Chart>
</div>
</template>

<script>
import Chart from "./components/Chart.vue";

export default {
  name: "app",
  components: {
    Chart
  }
};
</script>

<style>
body {
  font-size: 16pt;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  margin: 0 0 0 0;
}
h1 {
  font-size: 1.5rem;
  font-weight: 600;
  margin: 0 0 0 0;
  text-align: center;
}
.skinny {
  font-weight: 200;
}
.wrapper {
  display: grid;
}
header {
  display: grid;
  padding: 0.5rem 0 0.5rem 0;
  background: linear-gradient(-90deg, #3889a6, #2f9bc2);
  color: #ffffff;
  grid-template-columns: 1fr;
  align-items: center;
}

.menu-icon {
  padding: 0 0 0 1rem;
  font-size: 2rem;
}
</style>
