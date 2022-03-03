<template>
  <div class="modal">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 131 131"
      aria-labelledby="face"
      role="presentation"
      width="70"
      height="70"
      id="facesvg"
    >
      <title id="face">Face Icon</title>
      <defs></defs>
      <circle class="cls-1" cx="65.5" cy="65.5" r="64" />
      <circle class="cls-2" cx="95" cy="65.8" r="7.5" />
      <circle class="cls-2" cx="36" cy="65.8" r="7.5" />
      <path
        class="cls3"
        d="M51,97s6,10,23,10S95,97,95,97"
        transform="translate(-8.5 -5.5)"
      />
    </svg>
    <h3>{{ score > 0 ? "You Won" : "You Lost" }}</h3>
    <button @click="restart">Let's play again</button>
  </div>
</template>

<script>
import gsap from "gsap";
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["score"]),
  },
  methods: {
    restart() {
      this.$store.commit("restartGame");
    },
  },
  mounted() {
    if (Math.sign(this.score)) {
      gsap.to("#facesvg", {
        duration: 0.3,
        rotation: 180,
        transformOrigin: "50% 50%",
      });
    }
  },
};
</script>

<style lang="scss" scoped>
.cls-1 {
  fill: #fbb040;
  stroke: #231f20;
}

.cls-1,
.cls-3 {
  stroke-miterlimit: 10;
  stroke-width: 3px;
}

.cls-2 {
  fill: #231f20;
}

.cls-3 {
  fill: none;
  stroke: #be1e2d;
}
</style>
