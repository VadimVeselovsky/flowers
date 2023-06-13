<template>
  <div class="content-block-item section4">
    <audio loop src="/section4.m4a" ref="sound"></audio>
    <div :style="wrapperStyle" class="wrapper" v-if="show" @click="playSound">
      <div class="section4__container">
        <img
          :style="{ transform: transforms.img1 }"
          class="section4__img1"
          src="@/assets/images/section4/IMG_3824.webp"
        />
        <img
          :style="{ transform: transforms.img2 }"
          class="section4__img2"
          src="@/assets/images/section4/IMG_3825.avif"
        />
        <img
          :style="{ transform: transforms.img3 }"
          class="section4__img3"
          src="@/assets/images/section4/IMG_3826.avif"
        />
        <img
          :style="{ transform: transforms.img4 }"
          class="section4__img4"
          src="@/assets/images/section4/IMG_3827.avif"
        />
      </div>
      <div :style="{ transform: transforms.text }" class="section4__text3 text">
        the retroflection of his need to assert himself, and of his anger<br
          data-v-dfb9d4cf=""
        />in the compression of his abdominal and gastric musculature,<br
          data-v-dfb9d4cf=""
        />and in the withdrawal of energy from his shoulders and arms <br /><br />the act
        of compressing himself<br data-v-1df51d3b="" />
        kept on functioning as a physical symptom
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      transforms: {
        img1: null,
        img2: null,
        img3: null,
        img4: null,
        img5: null,
        text: null,
      },
      wrapperStyle: {
        top: null,
        bottom: null,
        position: null,
      },
    };
  },

  mounted() {
    document.addEventListener("scroll", this.onScroll);
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

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -1 < progress && progress <= 2;

      if (!this.show) return;

      if (-0.32 <= progress && progress < 0.6) this.playSound();
      else this.stopSound();

      if (-0.5 <= progress && progress < 0) {
        this.wrapperStyle.top = `calc(${-progress * 2}*50vh)`;
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

@keyframes opacity-flickering {
  1%,
  3%,
  8%,
  10% {
    opacity: 0.8;
  }
  4%,
  7%,
  11% {
    opacity: 1;
  }
}

.section4 {
  height: 1162px;

  &__container {
    position: absolute;
    left: calc(50% + -762px);
    top: 64px;
    width: 500px;
    height: 600px;
  }

  $animation-speed: 1.5s;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    width: 651px;
    top: calc(608px - 500px);
    left: calc(949px - 1000px);
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-timing-function: linear;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: 990px;
    left: calc(603px - 1000px);
    top: calc(258px - 500px);
    position: absolute;
    z-index: 2;
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.21s;
    animation-timing-function: linear;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 997px;
    top: calc(252px - 500px);
    position: absolute;
    z-index: 50;
    left: calc(598px - 1000px);
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.1s;
    animation-timing-function: linear;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    width: 318px;
    position: absolute;
    top: calc(589px - 500px);
    left: calc(1280px - 1000px);
    z-index: 2;
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.71s;
    animation-timing-function: linear;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 239px;
    top: -209px;
    width: 712px;
  }

  &__text3 {
    transform-origin: center;
    position: absolute;
    left: 919px;
    top: 679px;
  }
}
</style>
