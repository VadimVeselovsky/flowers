<template>
  <div class="content-block-item section5">
    <audio loop src="/flowers/section5.m4a" ref="sound"></audio>
    <div :style="wrapperStyle" class="wrapper" v-if="show" @click="playSound">
      <Teleport to="#indicators">
        <div style="left: 24rem">7</div>
      </Teleport>
      <div
        class="section5__first-plan"
        :style="{ transform: transforms.first_plan }"
      >
        <img
          :style="{ transform: transforms.first_plan_img8 }"
          class="section5__img8"
          src="@/assets/images/section5/IMG_1734.webp"
        />
        <img
          :style="{ transform: transforms.first_plan_img9 }"
          class="section5__img9"
          src="@/assets/images/section5/IMG_1735.webp"
        />
      </div>
      <div
        class="section5__second-plan"
        :style="{ transform: transforms.second_plan }"
      >
        <img
          class="section5__img3"
          src="@/assets/images/section5/IMG_3844.webp"
        />
        <img
          class="section5__img4"
          src="@/assets/images/section5/IMG_3845.webp"
        />
        <img
          class="section5__img7"
          src="@/assets/images/section5/IMG_3854.webp"
        />
      </div>
      <div
        class="section5__text2 text"
        :style="{ transform: transforms.third_plan }"
      >
        if he can feel accepted<br />and can finally allow himself to
        entrust,<br /><br />
        he will then be able to unfold<br />
        the blocked contact deliberateness<br /><br />
        and to gradually overcome the blocks<br />
        he has put<br /><br />
        between himself and the environment
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
          <img
            class="thin-spikelet__img3"
            src="@/assets/images/section5/IMG_3848.webp"
          />
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
    playSound() {
      const sound = this.$refs.sound;
      if (sound.paused) sound.play();
    },

    stopSound() {
      if (this.$refs.sound.paused) return;
      this.$refs.sound.currentTime = 0;
      this.$refs.sound.pause();
    },

    makeTransformsForStage(progress) {
      this.transforms.first_plan = `scale(${0.9 + progress * 1.7})`;
      this.transforms.second_plan = `scale(${0.6 + progress * 0.4})`;
      this.transforms.third_plan = `scale(${0.8 + progress * 0.2})`;
      this.transforms.first_plan_img8 = `translate(${
        (-progress * 100) / 19.2
      }vw, ${(-progress * 100) / 19.2}vw)`;
      this.transforms.first_plan_img9 = `translate(calc(${50 * progress}vw), ${
        (-progress * 100) / 19.2
      }vw)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight);

      this.show = -12 < progress;

      if (-0.9 <= progress) this.playSound();
      else this.stopSound();

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

$animation-speed: 10s;

@keyframes wind-1 {
  20% {
    transform: rotate(3deg);
  }
  40% {
    transform: rotate(4deg);
    animation-timing-function: ease-in-out;
  }
  66% {
    transform: rotate(-1deg);
    animation-timing-function: ease-out;
  }
}

@keyframes wind-2 {
  40% {
    transform: none;
    animation-timing-function: ease-out;
  }
  66% {
    transform: scale(0.995) rotate(4deg);
  }
}

@keyframes wind-3 {
  20% {
    transform: translate(1px, -2px) rotate(1deg);
  }
  40% {
    transform: translate(1px, -2px) rotate(1.1deg);
    animation-timing-function: ease-in-out;
  }
  66% {
    transform: rotate(-0.3deg);
    animation-timing-function: ease-out;
  }
}

.section5 {
  height: 100vw;

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
    width: 27.8vw;
    height: 38vw;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 30vw;
    top: 0.7vw;
    position: absolute;
    z-index: 50;
    left: calc(1417vw / 19.2);
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(1057vw / 19.2);
    top: 9.2vw;
    width: 25vw;
    z-index: 2;
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img7 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(1271vw / 19.2);
    width: 35.4vw;
    top: 14.3vw;
    z-index: 100;
    transform-origin: 51% 114%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img8 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: -13.5vw;
    width: 122.1vw;
    bottom: -75.8vw;
    z-index: 10;
  }

  &__img9 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    right: -6.5vw;
    width: 104.6vw;
    top: -13.7vw;
    z-index: 150;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(50% - 20.4vw);
    top: 10.4vw;
    width: 41.3vw;
    z-index: -1;
  }
}

.thin-spikelet {
  position: absolute;
  right: 93%;
  top: -8.854167vw;

  &__bone-1 {
    position: absolute;
    left: 2.7vw;
    top: -0.9vw;
    z-index: 3;
    width: 20.4vw;
    height: 37.2vw;
    transform-origin: 45% bottom;
    transform: rotate(-0.5deg);
    animation: wind-1 #{$animation-speed} infinite;
    animation-timing-function: ease;
  }

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 0.6vw;
    top: 17.4vw;
    width: 11.5vw;
    z-index: 3;
    transform-origin: 77% 92%;
    animation: wind-2 #{$animation-speed} infinite;
  }

  &__img2 {
    width: 18.3vw;
    left: 3.5vw;
    top: -1.2vw;
    position: absolute;
    z-index: 2;
    transform-origin: 36% 97%;
    animation-delay: -0.1s;
    animation: wind-3 #{$animation-speed} ease-in-out 0s infinite;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: -0.9vw;
    width: 21.4vw;
    top: 32.2vw;
    z-index: 2;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 5.8vw;
    width: 13.1vw;
    top: 23.9vw;
    z-index: 2;
  }
}
</style>
