<template>
  <div @click="toggleActive()" :class="{ 'dark-row': trackMode }">
    <div v-if="trackMode" class="split" :class="{ active: active }">
      {{ convertPace(pace * 0.24855) }}
    </div>
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
    <div class="full marathon-col" :class="{ active: active }">
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
    trackMode: Boolean,
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
<style>
.pace,
.five,
.ten,
.half,
.full,
.split {
  padding: 0.5rem 0 0.5rem 0;
  user-select: none;
  cursor: pointer;
  transition: background-color 0.6s ease, color 0.6s ease;
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

.split {
  width: 100%;
  background-color: #eeeeee;
  color: #FF1493;
  font-weight: 400;
}

/* Dark mode overrides */
.dark-row .pace,
.dark-row .ten,
.dark-row .full {
  background-color: #1a1a2e;
}
.dark-row .five,
.dark-row .half,
.dark-row .split {
  background-color: #16213e;
}
.dark-row .split {
  color: #FF1493;
}

.active {
  transition-duration: 0.3s;
  transition-timing-function: ease;
  background-color: rgba(255, 199, 0, 0.6);
  color: #000000;
}
.dark-row .active {
  background-color: rgba(255, 20, 147, 0.4);
  color: #ffffff;
}

@media only screen and (max-width: 600px) {
  .pace,
  .five,
  .ten,
  .half,
  .full,
  .split {
    padding: 0.35rem 0;
  }
}

@media only screen and (max-width: 500px) {
  .pace,
  .five,
  .ten,
  .half,
  .full,
  .split {
    padding: 0.25rem 0;
  }
}
</style>
