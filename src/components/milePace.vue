<template>
  <div @click="toggleActive()">
    <div class="pace" :class="{ active: active }">
      {{ convertPace(pace) }}
    </div>
    <div class="five" :class="{ active: active }">
      {{ convertTime5k(pace * 3.10686) }}
    </div>
    <div class="ten" :class="{ active: active }">
      {{ convertTime(pace * 6.21371) }}
    </div>
    <div class="half" :class="{ active: active }">
      {{ convertTime(pace * 13.1094) }}
    </div>
    <div class="full" :class="{ active: active }">
      {{ convertTime(pace * 26.2188) }}
    </div>
  </div>
</template>

<script>
export default {
  name: "MilePaceRow",
  components: {},
  props: {
    pace: Number,
    unit: Number,
  },
  data() {
    return {
      active: false,
    };
  },
  methods: {
    convertPace: function (value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(14, 5);
    },
    convertTime5k: function (value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(14, 5);
    },
    convertTime: function (value) {
      var date = new Date(null);
      date.setSeconds(value);
      return date.toISOString().substr(11, 8);
    },
    toggleActive: function () {
      this.active = !this.active;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style></style>
