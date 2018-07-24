<template>
<div @click="toggleActive()">
  <div class="pace"> {{ convertPace(pace) }} </div>
      <div class="five"> {{ convertTime5k(pace * 3.10686) }} </div>
      <div class="ten"> {{ convertTime(pace * 6.21371) }} </div>
      <div class="half"> {{ convertTime(pace * 13.1094) }} </div>
      <div class="full"> {{ convertTime(pace * 26.2188) }} </div>
</div>
</template>

<script>
export default {
  name: "milePace",
  components: {},
  props: {
    pace: Number,
    unit: Number,
    isActive: true
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
</style>
