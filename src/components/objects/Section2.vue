<template>
  <div class="content-block-item section2">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <Teleport to="#indicators">
        <div style="left: 20rem">6: {{ (progress * 100).toFixed(0) }}</div>
      </Teleport>
      <img
        :style="{ transform: transforms.img1 }"
        class="section2__img1"
        src="@/assets/images/section2/1.webp"
      />
      <video
        :style="{ transform: transforms.img2 }"
        class="section2__img2"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/2.webm" type="video/webm" />
      </video>
      <video
        :style="{ transform: transforms.img3 }"
        class="section2__img3"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/3_.webm" type="video/webm" />
      </video>
      <video class="section2__img4" autoplay loop muted>
        <source src="@/assets/images/section2/4.webm" type="video/webm" />
      </video>
      <div
        class="section2__text1 text"
        :style="{ transform: transforms.text1 }"
      >
        when the movement directed towards the environment<br />
        is physically inhibited as soon as it starts
      </div>
      <div class="section2__text2 text">
        the blocked action manifests itself <br />
        as tension and immobility in the muscular groups involved.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      progress: 0,
      show: false,
      counter: 0,
      transforms: {
        img1: null,
        img2: null,
        img3: null,
        text1: null,
      },
      wrapperStyle: {
        transform: null,
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
    makeTransformsForStage(progress) {
      const inverse = 1 - progress;

      this.transforms.img1 = `scale(${1 - 0.2 * inverse}) translate(-${
        (90 + inverse * 682) / 19.2
      }vw, -${(80 + inverse * 946) / 19.2}vw) rotate(${53 - 14 * inverse}deg)`;
      this.transforms.img2 = `scale(${1.4 + 0.72 * inverse}) translate(-${
        (24 + 145 * inverse) / 19.2
      }vw, ${(-155 + 238 * inverse) / 19.2}vw) rotate(${5 * progress}deg)`;
      this.transforms.img3 = `scale(${0.82 - 0.33 * inverse}) translate(${
        (-23 + inverse * 1139) / 19.2
      }vw, -${(379 + inverse * 151) / 19.2}vw) rotate(${47 - 2 * inverse}deg)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -4 < progress && progress <= 2.3;

      if (!this.show) return;

      this.progress = progress;

      if (progress < 0) this.makeTransformsForStage(0);

      if (0 <= progress && progress <= 1) {
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        if (this.counter++ % 4 === 0) this.makeTransformsForStage(progress);

        this.wrapperStyle.transform = null;
        this.wrapperStyle.position = "fixed";
      } else if (1 < progress && progress <= 2) {
        this.wrapperStyle.position = "fixed";
        this.wrapperStyle.top = 0;
        this.wrapperStyle.transform =
          "translateY(" +
          (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) * rect.height * 1 +
          "px)";
        this.makeTransformsForStage(1);
      } else {
        this.wrapperStyle.position = "absolute";
        this.wrapperStyle.transform = null;
      }

      if (-0.5 <= progress && progress < 0) {
        this.wrapperStyle.top = `calc(${-progress * 1}*20vw)`;
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
}
.section2 {
  height: calc(3000vw / 19.2);
  z-index: 200;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(2000vw / 19.2);
    top: calc(2vw / 19.2);
    position: absolute;
    right: calc(-785vw / 19.2);
    z-index: 50;
    // transform: rotate(50deg);
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(569vw / 19.2);
    top: calc(60vw / 19.2);
    position: absolute;
    right: calc(-26.5vw / 19.2);
    z-index: 4;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(4150vw / 19.2);
    top: calc(-375vw / 19.2);
    position: absolute;
    left: calc(-1864vw / 19.2);
    z-index: 5;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1291vw / 19.2);
    top: calc(1011vw / 19.2);
    position: absolute;
    right: calc(92vw / 19.2);
    z-index: 50;
    transform: rotate(3deg);
  }

  &__img5 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(500vw / 19.2);
    bottom: calc(-110vw / 19.2);
    left: 0;
    position: absolute;
    z-index: 2;
  }

  &__text1 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    position: absolute;
    left: 38.04vw;
    top: 22.88vw;
    width: 63.59vw;
    z-index: 4;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    position: absolute;
    left: 50%;
    top: 65.93vw;
    width: 69.27vw;
    transform: translateX(-45%);
  }
}
</style>
