<template>
  <div class="content-block-item section5">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <div class="thin-spikelet section5__spikelet-1">
        <div class="thin-spikelet__bone-1">
          <img class="thin-spikelet__img1" src="@/assets/images/section5/IMG_3842.webp" />
          <img class="thin-spikelet__img2" src="@/assets/images/section5/IMG_3843.png" />
          <img class="thin-spikelet__img4" src="@/assets/images/section5/IMG_3849.webp" />
        </div>
        <img class="thin-spikelet__img3" src="@/assets/images/section5/IMG_3848.webp" />
      </div>
      <img class="section5__img3" src="@/assets/images/section5/IMG_3844.webp" />
      <img class="section5__img4" src="@/assets/images/section5/IMG_3845.webp" />
      <img class="section5__img7" src="@/assets/images/section5/IMG_3854.webp" />
      <div class="section5__text2">
        if he can feel accepted<br />and can finally allow himself to entrust,<br /><br /><br />
        he will then be able to unfold the blocked contact deliberateness<br /><br />
        and to gradually overcome the blocks he has put<br /><br />
        between himself and the environment
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      wrapperStyle: {
        top: null,
        bottom: null,
        position: null,
      },
    };
  },

  mounted() {
    document.addEventListener("scroll", this.onScroll);
    this.onScroll();
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress;

      if (!this.show) return;
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  position: absolute;
  height: 100%;
  width: 100%;
  top: 0;
  z-index: 100;
}

$animation-speed: 3s;

@keyframes wind-1 {
  25% {
    transform: rotate(4deg);
  }
  50% {
    transform: rotate(-5deg);
  }
  75% {
    transform: rotate(5deg);
  }
}

@keyframes wind-2 {
  24% {
    transform: rotate(0.7deg);
  }
  48% {
    transform: rotate(-1deg);
  }
  74% {
    transform: rotate(1deg);
  }
}

@keyframes wind-3 {
  20% {
    transform: rotate(1deg);
  }
  40% {
    transform: rotate(-1deg);
  }
  67% {
    transform: rotate(2deg);
  }
}

.section5 {
  height: 880px;
  overflow: hidden;

  &__spikelet-1 {
    left: 100px;
    top: 0;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 570px;
    top: 7px;
    position: absolute;
    z-index: 50;
    left: calc(50% + 1360px - 951px);
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1159px - 951px);
    top: 174px;
    width: 475px;
    z-index: 2;
  }

  &__img7 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1223px - 951px);
    width: 673px;
    top: 262px;
    z-index: 100;
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} ease-in-out 0.3s infinite;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 562px - 951px);
    top: 97px;
    font-size: 42.5px;
    width: 786px;
    line-height: 1.3;
  }
}

.thin-spikelet {
  position: relative;
  &__bone-1 {
    position: absolute;
    left: 0px;
    z-index: 3;
    width: 389px;
    height: 707px;
    transform-origin: 45% bottom;
    animation: wind-1 #{$animation-speed} ease-in-out 0s infinite;
  }

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(111px - 100px);
    top: 331px;
    width: 218px;
    z-index: 3;
    transform-origin: 77% 87%;
    animation: wind-2 #{$animation-speed} ease-in-out 0s infinite;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: 349px;
    left: calc(129px - 100px);
    top: -8px;
    position: absolute;
    z-index: 2;
    transform-origin: 36% 97%;
    animation: wind-3 #{$animation-speed} ease-in-out 0s infinite;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(83px - 100px);
    width: 408px;
    top: 612px;
    z-index: 2;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(210px - 100px);
    width: 249px;
    top: 454px;
    z-index: 2;
  }
}
</style>
