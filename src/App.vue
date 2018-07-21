<template>
<div class="wrapper">
  <header>
    <img src="./assets/pace2.svg" width="389px" height="100px" >
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
  font-family: "Open Sans", sans-serif;
  margin: 0 0 0 0;
}
h1 {
  font-size: 1.5rem;
  font-weight: 400;
  margin: 0 0 0 0;
  text-align: center;
}
.skinny {
  font-weight: 300;
}
.wrapper {
  display: grid;
}
header {
  display: grid;
  padding: 0.5rem 0 0.5rem 0;
  background: #ffffff;
  grid-template-columns: 1fr;
  height: 132px;
  align-items: center;
  justify-items: center;
}

.menu-icon {
  padding: 0 0 0 1rem;
  font-size: 2rem;
}
</style>
