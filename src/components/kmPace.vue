<template>
<div @click="toggleActive()" >
  <div class="pace" :class="{ 'active': isActive }"> {{ convertPace(pace) }} </div>
      <div class="five" :class="{ 'active': isActive }"> {{ convertTime5k(pace * 5) }} </div>
      <div class="ten" :class="{ 'active': isActive }"> {{ convertTime(pace * 10) }} </div>
      <div class="half" :class="{ 'active': isActive }"> {{ convertTime(pace * 21.0975) }} </div>
      <div class="full" :class="{ 'active': isActive }"> {{ convertTime(pace * 42.195) }} </div>
</div>
</template>

<script>
export default {
  name: "kmPace",
  components: {},
  props: {
    pace: Number,
    unit: Number,
    isActive: false
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
    },
    toggleStyle: function(value) {
      value.isActive = !value.isActive;
    },
    toggleActive: function() {
      this.isActive = !this.isActive;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.pace,
.five,
.ten,
.half,
.full {
  padding: 0.5rem 0 0.5rem 0;
  user-select: none;
  cursor: pointer;
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

.active {
  transition-duration: 0.3s;
  transition-timing-function: ease;
  background-color: rgba(255, 199, 0, 0.6);
  color: #000000;
}
</style>
