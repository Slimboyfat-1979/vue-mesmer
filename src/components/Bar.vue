<template>
  <div
    :class="[
      barName,
      { start: showStarted, paused: animationState === 'paused' },
    ]"
    :style="{ backgroundColor: color }"
  ></div>
</template>

<script>
export default {
  props: ["color", "barName", "animationState"],
  data() {
    return {
      showStarted: false, // control start of animation
    };
  },
  mounted() {
    // Start the animation when the component mounts
    this.showStarted = true;
  },
};
</script>

<style scoped>
div {
  position: absolute;
  height: 60px;
  width: 100px;
  left: 100%;
}

div.start {
  animation: move 90s linear infinite forwards;
}

div.paused {
  animation-play-state: paused;
}

.one {
  top: 40%;
}

.two {
  top: 60%;
}

@keyframes move {
  0% {
    left: 100%;
  }
  50% {
    left: 0;
  }
  100% {
    left: 100%;
  }
}
</style>
