<template>
  <div class="content-block-item section6">
    <audio loop src="/flowers/section6.m4a" ref="sound"></audio>
    <div :style="wrapperStyle" class="wrapper" v-if="show" @click="playSound">
      <Teleport to="#indicators">
        <div style="left: 12rem">4</div>
      </Teleport>
      <video class="section6__img6" autoplay loop muted>
        <source
          src="@/assets/images/section6/animation1.webm"
          type="video/webm"
        />
      </video>
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

      this.show = -1 < progress && progress < 2;

      if (-0.1 <= progress && progress < 0.5) this.playSound();
      else this.stopSound();

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

.section6 {
  height: calc(3209vw / 19.2);
  overflow: hidden;

  &__img6 {
    position: absolute;
    top: calc(-383vw / 19.2);
    left: calc(1490vw / 19.2);
    width: calc(3928vw / 19.2);
    transform: translateX(-50%);
  }
}
</style>
