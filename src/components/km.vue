<template>
  <div :class="{ 'dark-mode': trackMode }">
    <nav>
      <button v-on:click="unit = 0" type="submit">🔥 Kilometres</button>
      <button v-on:click="unit = 1" type="submit">🔥 Miles</button>
    </nav>
    <div v-if="unit === 0" class="row top" :class="{ 'row-6': trackMode, 'top-dark': trackMode }">
      <div v-if="trackMode" class="split-header">400m</div>
      <div>1km</div>
      <div>5km</div>
      <div>10km</div>
      <div>21.1km</div>
      <div class="marathon-col">42.2km</div>
    </div>

    <div v-if="unit === 1" class="row top" :class="{ 'row-6': trackMode, 'top-dark': trackMode }">
      <div v-if="trackMode" class="split-header">400m</div>
      <div>1 Mile</div>
      <div>3.1m</div>
      <div>6.2m</div>
      <div>13.1m</div>
      <div class="marathon-col">26.2m</div>
    </div>

    <template v-if="unit === 0">
      <div v-for="pace in kmPaces" :key="pace">
        <kmPace :unit="unit" :pace="pace" :trackMode="trackMode" class="row" :class="{ 'row-6': trackMode }"></kmPace>
      </div>
    </template>

    <template v-if="unit === 1">
      <div v-for="pace in milePaces" :key="pace">
        <milePace :unit="unit" :pace="pace" :trackMode="trackMode" class="row" :class="{ 'row-6': trackMode }"></milePace>
      </div>
    </template>
  </div>
</template>
<script>
import kmPace from "./kmPace.vue";
import milePace from "./milePace.vue";

const range = (start, length) =>
  Array.from(Array(length).keys()).map((v, i) => start + i * 5);

export default {
  name: "PaceGrid",
  components: {
    kmPace,
    milePace,
  },
  props: {
    trackMode: Boolean,
  },
  data: function () {
    return {
      kmPaces: range(130, 80),
      milePaces: range(210, 80),
      unit: 0,
    };
  },
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
h1 {
  color: hsl(0, 0%, 90%);
}
nav {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 0.5rem;
  justify-content: center;
  align-content: center;
  margin: 0rem 0 1rem 0;
  max-width: 320px;
  margin-left: auto;
  margin-right: auto;
}
.row {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  font-size: 1.2rem;
  text-align: center;
  color: #6c6c6c;
  transition: grid-template-columns 0.4s ease;
}
.row-6 {
  grid-template-columns: repeat(6, 1fr);
}
.dark-mode .row {
  color: #c0c0c0;
}

.top {
  background-color: rgba(255, 255, 255, 0.85);
  height: 3rem;
  align-items: center;
  font-size: 1.4rem;
  color: #5c5c5c;
  position: sticky;
  top: 0;
  transition: background-color 0.6s ease, color 0.6s ease;
}
.top-dark {
  background-color: rgba(26, 26, 46, 0.95);
  color: #e0e0e0;
}

.split-header {
  color: #FF1493;
  font-weight: 400;
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
  transition: background-color 0.4s ease, color 0.4s ease;
}
.dark-mode button {
  color: #c0c0c0;
  box-shadow: 0 2px 5px 0 hsla(0, 0%, 0%, 0.4);
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
.dark-mode button:hover {
  background-color: #FF1493;
  color: #fff;
}

@media only screen and (max-width: 600px) {
  .row {
    font-size: 0.85rem;
  }
  .row-6 {
    font-size: 0.78rem;
  }
  .top {
    font-size: 1rem;
    height: 2.5rem;
  }
  nav {
    max-width: 270px;
  }
  button {
    font-size: 0.85rem;
    padding: 0.4rem 0.3rem 4px 0.3rem;
  }
}

@media only screen and (max-width: 480px) {
  .row {
    font-size: 0.72rem;
  }
  .row-6 {
    grid-template-columns: repeat(5, 1fr);
    font-size: 0.72rem;
  }
  .row-6 .marathon-col {
    display: none;
  }
  .top {
    font-size: 0.8rem;
    height: 2.2rem;
  }
  nav {
    max-width: 240px;
    grid-gap: 0.3rem;
    margin-bottom: 0.5rem;
  }
  button {
    font-size: 0.75rem;
    padding: 0.35rem 0.2rem 3px 0.2rem;
  }
}
</style>
