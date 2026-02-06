<template>
  <div class="wrapper" :class="{ 'dark-mode': trackMode }">
    <!-- Track Mode vertical accordion button -->
    <div class="track-mode-tab" :class="{ active: trackMode }" @click="toggleTrackMode">
      <span class="track-mode-label">T R A C K &nbsp; M O D E</span>
    </div>

    <!-- Let's go! flash overlay -->
    <div
      v-if="showFlash"
      class="flash-overlay"
      @animationend="showFlash = false"
    >Let's go!</div>

    <header>
      <svg
        class="logo-svg"
        viewBox="0 0 389 100"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect
          :stroke="trackMode ? '#FF1493' : '#FFC700'"
          stroke-width="2"
          fill="none"
          x="1"
          y="1"
          width="387"
          height="98"
        />
        <text
          font-family="HelveticaNeue-UltraLight, Helvetica Neue"
          font-size="72"
          font-weight="200"
          :fill="trackMode ? '#FF1493' : '#FFC700'"
        >
          <tspan x="32" y="75">Pace Chart</tspan>
        </text>
      </svg>
    </header>
    <Chart :trackMode="trackMode"></Chart>
  </div>
</template>

<script>
import Chart from "./components/Chart.vue";

export default {
  name: "app",
  components: {
    Chart,
  },
  data() {
    return {
      trackMode: false,
      showFlash: false,
    };
  },
  methods: {
    toggleTrackMode() {
      this.trackMode = !this.trackMode;
      if (this.trackMode) {
        this.showFlash = true;
      }
    },
  },
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
  max-width: 100vw;
  overflow-x: hidden;
  transition: background-color 0.6s ease, color 0.6s ease;
}
.wrapper.dark-mode {
  background-color: #1a1a2e;
  color: #e0e0e0;
}
header {
  display: grid;
  padding: 0.5rem 0 0.5rem 0;
  background: inherit;
  grid-template-columns: 1fr;
  height: 132px;
  align-items: center;
  justify-items: center;
  transition: background-color 0.6s ease;
}
.logo-svg {
  width: 389px;
  height: auto;
  max-width: 80vw;
}
.logo-svg rect,
.logo-svg text {
  transition: stroke 0.6s ease, fill 0.6s ease;
}

/* Track Mode vertical tab */
.track-mode-tab {
  position: fixed;
  left: 0;
  top: 0;
  bottom: 0;
  margin: auto 0;
  height: fit-content;
  z-index: 100;
  background-color: #ffc700;
  color: #333;
  writing-mode: vertical-rl;
  text-orientation: mixed;
  padding: 14px 6px;
  cursor: pointer;
  border-radius: 0 6px 6px 0;
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 2px;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.15);
  transition: background-color 0.4s ease, color 0.4s ease, box-shadow 0.3s ease;
  user-select: none;
}
.track-mode-tab:hover {
  box-shadow: 2px 2px 12px rgba(0, 0, 0, 0.3);
}
.track-mode-tab.active {
  background-color: #FF1493;
  color: #fff;
}
.track-mode-label {
  pointer-events: none;
}

/* Let's go! flash overlay */
.flash-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  font-weight: 700;
  color: #FF1493;
  z-index: 200;
  pointer-events: none;
  letter-spacing: 4px;
  animation: flash-in-out 1.5s ease forwards;
}
@keyframes flash-in-out {
  0% {
    opacity: 0;
    transform: scale(0.8);
  }
  15% {
    opacity: 1;
    transform: scale(1.05);
  }
  30% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: scale(1);
  }
}

/* Mobile responsiveness */
@media only screen and (max-width: 600px) {
  header {
    height: 100px;
    padding: 0.4rem 0;
  }
  .logo-svg {
    width: 280px;
  }
  .track-mode-tab {
    padding: 10px 5px;
    font-size: 0.6rem;
    letter-spacing: 1px;
  }
  .flash-overlay {
    font-size: 2rem;
    letter-spacing: 2px;
  }
}

@media only screen and (max-width: 500px) {
  header {
    height: 80px;
    padding: 0.3rem 0;
  }
  .logo-svg {
    width: 220px;
  }
  .track-mode-tab {
    padding: 8px 4px;
    font-size: 0.55rem;
    letter-spacing: 1px;
  }
  .flash-overlay {
    font-size: 1.5rem;
    letter-spacing: 1px;
  }
}

@media only screen and (max-width: 360px) {
  .track-mode-tab {
    padding: 6px 3px;
    font-size: 0.45rem;
    letter-spacing: 0px;
    border-radius: 0 4px 4px 0;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.15);
  }
}

.menu-icon {
  padding: 0 0 0 1rem;
  font-size: 2rem;
}
</style>
