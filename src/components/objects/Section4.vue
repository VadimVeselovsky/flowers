<template>
  <div class="content-block-item section4">
    <audio loop src="/flowers/section4.m4a?t=2" ref="sound"></audio>
    <div :style="wrapperStyle" class="wrapper" v-if="show" @click="playSound">
      <Teleport to="#indicators">
        <div style="left: 8rem">3</div>
      </Teleport>
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
        <i>
          his need to assert himself<br />
          and his anger<br />
          in the compression of his abdominal<br />and gastric musculature<br />
          <br />
          and in the withdrawal of energy<br />
          from his shoulders and arms
        </i>
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

      if (-0.32 <= progress && progress < 0.5) this.playSound();
      else this.stopSound();

      if (!this.show) return;

      if (progress < 0) {
        this.wrapperStyle.top = `calc(${-progress * 2}*50vh)`;
      } else {
        this.wrapperStyle.top = "0";
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
  height: 63.520833vw;

  &__container {
    position: absolute;
    left: calc(198vw / 19.2);
    top: 12.333333vw;
    width: calc(500vw / 19.2);
    height: calc(600vw / 19.2);
  }

  $animation-speed: 1.5s;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    width: calc(651vw / 19.2);
    top: calc(108vw / 19.2);
    left: calc(-51vw / 19.2);
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-timing-function: linear;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: calc(990vw / 19.2);
    left: calc(-397vw / 19.2);
    top: calc(-242vw / 19.2);
    position: absolute;
    z-index: 2;
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.21s;
    animation-timing-function: linear;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: calc(997vw / 19.2);
    top: calc(-248vw / 19.2);
    position: absolute;
    z-index: 50;
    left: calc(-402vw / 19.2);
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.1s;
    animation-timing-function: linear;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    width: calc(318vw / 19.2);
    position: absolute;
    top: calc(89vw / 19.2);
    left: calc(280vw / 19.2);
    z-index: 2;
    animation: opacity-flickering #{$animation-speed} infinite;
    animation-delay: 0.71s;
    animation-timing-function: linear;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: calc(239vw / 19.2);
    top: calc(-209vw / 19.2);
    width: calc(712vw / 19.2);
  }

  &__text3 {
    transform-origin: center;
    position: absolute;
    left: 59.864583vw;
    bottom: 6.604167vw;
  }
}
</style>
