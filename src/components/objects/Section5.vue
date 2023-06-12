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

      if (0 <= progress && progress <= 1) {
        // progress *= 2;
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        if (this.counter++ % 4 === 0) this.makeTransformsForStage(progress);
        this.wrapperStyle.position = "fixed";
      } else {
        this.wrapperStyle.position = "absolute";
        this.wrapperStyle.transform = null;
      }
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

$animation-speed: 7s;

@keyframes wind-1 {
  10% {
    animation-timing-function: cubic-bezier(.19,.17,.62,.86);
    transform: skewX(-1.3deg) rotate(1.3deg);
  }
  35% {
    animation-timing-function: ease-in;
    transform: none;
  }
  // 80% {
  // transform: skewX(0.5deg) rotate(-1deg);
  // }
  // 90% {
  // transform: skewX(-0.3deg) rotate(0.5deg);
  // }
}

// @keyframes wind-2 {
// 15% {
// transform: skewX(-0.5deg) rotate(1deg);
// }
// 80% {
// transform: skewX(0.1deg) rotate(-0.2deg);
// }
// 92% {
// transform: skewX(-0.05deg) rotate(0.1deg);
// }
// }

@keyframes wind-3 {
  10% {
    animation-timing-function: cubic-bezier(0.19, 0.17, 0.75, 0.8);
    transform: skewX(-2deg) rotate(2deg);
  }
  35% {
    animation-timing-function: ease-in;
    transform: none;
  }
  // 17% {
  // transform: skewX(-2deg) rotate(1deg);
  // }
  // 80% {
  // transform: skewX(0.5deg) rotate(-0.7deg);
  // }
  // // 92% {
  // transform: skewX(-0.2deg) rotate(0.3deg);
  // }
}

.section5 {
  height: 200vh;
  overflow: hidden;

  &__spikelet-1 {
    left: 100px;
    top: 100px;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 570px;
    top: 107px;
    position: absolute;
    z-index: 50;
    left: calc(50% + 1360px - 951px);
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1159px - 951px);
    top: 274px;
    width: 475px;
    z-index: 2;
  }

  &__img7 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1223px - 951px);
    width: 673px;
    top: 362px;
    z-index: 100;
    transform-origin: 51% 114%;
    // animation: wind-2 #{$animation-speed} infinite;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 562px - 951px);
    top: 197px;
    font-size: 42.5px;
    width: 786px;
    line-height: 1.3;
  }
}

.thin-spikelet {
  position: relative;
  &__bone-1 {
    position: absolute;
    left: 52px;
    top: -17px;
    z-index: 3;
    width: 389px;
    height: 707px;
    transform-origin: 45% bottom;
    animation: wind-1 #{$animation-speed} infinite;
  }

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(111px - 100px);
    top: 331px;
    width: 218px;
    z-index: 3;
    transform-origin: 77% 92%;
    animation: wind-2 #{$animation-speed} infinite;
    animation-delay: -0.15s;
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
    animation-delay: -0.24s;
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
