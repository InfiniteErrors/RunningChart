<template>
  <div>
    <nav>
    <button v-on:click="unit = 0" type="submit">🔥 Kilometres</button>
    <button v-on:click="unit = 1" type="submit">🔥 Miles</button>
    </nav>
    <div v-if="unit === 0" class="row top">
      <div> 1km </div>
      <div> 5km </div>
      <div> 10km </div>
      <div> 21.1km </div>
      <div> 42.2km </div>
    </div>

    <div v-if="unit === 1" class="row top">
      <div> 1 Mile </div>
      <div> 3.1m </div>
      <div> 6.2m</div>
      <div> 13.1m</div>
      <div> 26.2m </div>
    </div>

    <div v-if="unit === 0" v-for="kmPace in kmPaces">
      <kmPace :unit="unit" :pace="kmPace" class="row"></kmPace>
    </div>

    <div v-if="unit === 1" v-for="milePace in milePaces">
      <milePace :unit="unit" :pace="milePace" class="row"></milePace>
    </div>

  </div>
</template>
<script>
import kmPace from "./kmPace.vue";
import milePace from "./milePace.vue";

const range = (start, length) =>
  Array.from(Array(length).keys()).map((v, i) => start + i * 5);

export default {
  name: "km",
  components: {
    kmPace,
    milePace
  },
  data: function() {
    return {
      kmPaces: range(155, 66),
      milePaces: range(230, 70),
      unit: 0
    };
  },
  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1 {
  color: hsl(0, 0%, 90%);
}
nav {
  display: grid;
  grid-template-columns: 150px 150px;
  grid-gap: 0.5rem;
  justify-content: center;
  align-content: center;
  margin: 0rem 0 1rem 0;
}
.row {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  font-size: 1.2rem;
  text-align: center;
  color: #6c6c6c;
}

.top {
  background-color: rgba(255, 255, 255, 0.85);
  height: 3rem;
  align-items: center;
  font-size: 1.4rem;
  color: #5c5c5c;
  position: sticky;
  top: 0;
}

button {
  background: none;
  border: none;
  box-shadow: 0 2px 5px 0 hsla(0, 0%, 0%, 0.2);
  border-radius: 4px;
  font-size: 1rem;
  padding: 0.5rem 0.5rem 5px 0.5rem;
  font-size: 1rem;
  color: #8c8c8c;
  outline: none;
}

button:focus {
  outline: none;
}

button:hover {
  transition-duration: 0.5s;
  transition-timing-function: ease;
  background-color: #ffc700;
  cursor: pointer;
}

@media only screen and (max-width: 445px) {
  .row {
    font-size: 0.9rem;
  }
  .top {
    font-size: 1.1rem;
  }
  nav {
    grid-template-columns: 125px 125px;
  }
  img {
    width: 300px;
  }
}
</style>
