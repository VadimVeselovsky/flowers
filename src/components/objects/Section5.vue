<template>
  <div class="content-block-item section5">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <div class="section5__first-plan" :style="{ transform: transforms.first_plan }">
        <img
          :style="{ transform: transforms.first_plan_img8 }"
          class="section5__img8"
          src="@/assets/images/section5/IMG_1734.png"
        />
        <img
          :style="{ transform: transforms.first_plan_img9 }"
          class="section5__img9"
          src="@/assets/images/section5/IMG_1735.png"
        />
      </div>
      <div class="section5__second-plan" :style="{ transform: transforms.second_plan }">
        <div class="thin-spikelet section5__spikelet-1">
          <div class="thin-spikelet__bone-1">
            <img
              class="thin-spikelet__img1"
              src="@/assets/images/section5/IMG_3842.webp"
            />
            <img
              class="thin-spikelet__img2"
              src="@/assets/images/section5/IMG_3843.png"
            />
            <img
              class="thin-spikelet__img4"
              src="@/assets/images/section5/IMG_3849.webp"
            />
          </div>
          <img class="thin-spikelet__img3" src="@/assets/images/section5/IMG_3848.webp" />
        </div>
        <img class="section5__img3" src="@/assets/images/section5/IMG_3844.webp" />
        <img class="section5__img4" src="@/assets/images/section5/IMG_3845.webp" />
        <img class="section5__img7" src="@/assets/images/section5/IMG_3854.webp" />
        <div class="section5__text2 text">
          if he can feel accepted<br />and can finally allow himself to entrust,<br /><br />
          he will then be able to unfold<br />
          the blocked contact deliberateness<br /><br />
          and to gradually overcome the blocks<br />
          he has put<br /><br />
          between himself and the environment
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      transforms: {},
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
    makeTransformsForStage(progress) {
      this.transforms.first_plan = `scale(${0.9 + progress * 1.2})`;
      this.transforms.second_plan = `scale(${0.6 + progress * 0.4})`;
      this.transforms.first_plan_img8 = `translate(${-progress * 100}px, ${
        -progress * 100
      }px)`;
      this.transforms.first_plan_img9 = `translate(${progress * 100}px, ${
        -progress * 100
      }px)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight);

      this.show = -2 < progress;

      if (!this.show) return;

      if (progress < 0) {
        this.makeTransformsForStage(0);
      }
      if (0 <= progress && progress <= 1.1) {
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.makeTransformsForStage(progress);
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
  20% {
    transform: scale(1.015) skewX(-3deg) rotate(3deg);
  }
  40% {
    transform: scale(1.013) skewX(-3.2deg) rotate(3.2deg);
    animation-timing-function: ease-in-out;
  }
  66% {
    transform: scale(0.995) skewX(1deg) rotate(-1deg);
    animation-timing-function: ease-out;
  }
}

@keyframes wind-2 {
  40% {
    transform: none;
    animation-timing-function: ease-out;
  }
  66% {
    transform: scale(0.995) skewX(0.5deg) rotate(-1deg);
  }
}

@keyframes wind-3 {
  21% {
    transform: scale(1.01) skewX(-0.2deg) rotate(0.5deg);
  }
  40% {
    transform: skewX(0.05deg) rotate(-0.05deg);
  }
}

.section5 {
  height: 200vh;

  &__second-plan {
    position: absolute;
    width: 100%;
    height: 100vh;
  }
  &__first-plan {
    position: absolute;
    width: 100%;
    height: 100vh;
    z-index: 150;
  }

  &__spikelet-1 {
    width: 530px;
    height: 723px;
    left: calc(50% - 868px);
    top: 26px;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 570px;
    top: 14px;
    position: absolute;
    z-index: 50;
    left: calc(50% + 1360px - 951px);
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1159px - 951px);
    top: 175px;
    width: 475px;
    z-index: 2;
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img7 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 1223px - 951px);
    width: 673px;
    top: 273px;
    z-index: 100;
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img8 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: -256px;
    width: 2323px;
    bottom: -1443px;
    z-index: 10;
  }

  &__img9 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    right: -124px;
    width: 1990px;
    top: -261px;
    z-index: 150;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% + 562px - 951px);
    top: 197px;
    width: 786px;
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
    transform: skewX(0.5deg) rotate(-0.5deg);
    animation: wind-1 #{$animation-speed} infinite;
    animation-timing-function: ease;
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
    // animation: wind-3 #{$animation-speed} ease-in-out 0s infinite;
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
