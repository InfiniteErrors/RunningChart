<template>
  <div>
    <nav>
    <button v-on:click="view = 0" type="submit">🇨🇦 Kilometres</button>
    <button v-on:click="view = 1" type="submit">🇺🇸 Miles</button>
    </nav>

    <div v-if="view === 0" class="row top">
      <div> 1km </div>
      <div> 5km </div>
      <div> 10km </div>
      <div> 21km </div>
      <div> 42km </div>
    </div>

    <div v-if="view === 1" class="row top">
      <div> 1 Mile </div>
      <div> 3.1m </div>
      <div> 6.2m</div>
      <div> 13.1m</div>
      <div> 26.2m </div>
    </div>

    <div class="row" v-for="pace in paces">
      <div v-if="view === 0" class="pace"> {{ convertPace(pace) }} </div>
      <div v-if="view === 1" class="pace"> {{ convertPace(pace * 1.621) }} </div>
      <div class="five"> {{ convertTime5k(pace * 5) }} </div>
      <div class="ten"> {{ convertTime(pace * 10) }} </div>
      <div class="half"> {{ convertTime(pace * 21.0975) }} </div>
      <div class="full"> {{ convertTime(pace * 42.195) }} </div>
    </div>

  </div>
</template>
<script>
const range = (start, length) =>
  Array.from(Array(length).keys()).map((v, i) => start + i * 5);

export default {
  name: "km",
  data: function() {
    return {
      paces: range(155, 66),
      view: 0
    };
  },
  methods: {
    convertPace: function(value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(14, 5);
    },
    convertTime5k: function(value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(14, 5);
    },
    convertTime: function(value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(11, 8);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: hsl(0, 0%, 90%);
}
nav {
  display: grid;
  grid-template-columns: 150px 150px;
  grid-gap: 0.5rem;
  justify-content: center;
  align-content: center;
  margin: 2rem 0 2rem 0;
}
.row {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  font-size: 1rem;
  text-align: center;
  color: #526b7f;
}

.pace,
.five,
.ten,
.half,
.full {
  padding: 0.5rem 0 0 0;
}

.pace {
  width: 100%;
  background-color: #ffffff;
}

.five {
  width: 100%;
  background-color: #eeeeee;
}

.ten {
  width: 100%;
  background-color: #ffffff;
}

.half {
  width: 100%;
  background-color: #eeeeee;
}

.full {
  width: 100%;
  background-color: #ffffff;
}

.top {
  background-color: #ffffff;
  margin: 0 0 1.5rem 0;
  font-size: 1.2rem;
  color: #526b7f;
  position: sticky;
  top: 0;
}

button {
  background: none;
  border: 1px solid #3889a6;
  border-radius: 4px;
  font-size: 1.25em;
  padding: 0.5rem 0.5rem 5px 0.5rem;
  font-size: 1rem;
  color: #526b7f;
}

button:hover {
  transition-duration: 0.5s;
  transition-timing-function: ease;
  background-color: #3889a6;
  color: #ffffff;
  cursor: pointer;
}
</style>
