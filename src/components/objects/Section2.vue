<template>
  <div class="content-block-item section2">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <Teleport to="#indicators">
        <div style="left: 20rem">6: {{ (progress * 100).toFixed(0) }}</div>
      </Teleport>
      <img
        :style="{ transform: transforms.img1, ...styles.img1 }"
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
        :style="{ transform: transforms.img3, ...styles.img3 }"
        class="section2__img3"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/3_.webm" type="video/webm" />
      </video>
      <video :style="styles.img4" class="section2__img4" autoplay loop muted>
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
        as tension and immobility in the muscular groups involved
      </div>
    </div>
  </div>
</template>

<script>
import { throttle } from "lodash-es";

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
        img4: null,
        text1: null,
      },
      styles: {
        img1: {},
        img3: {},
        img4: {},
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
    makeTransformsForStage: throttle(function (progress) {
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
    }, 100),

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -4 < progress && progress <= 2.3;

      if (!this.show) return;

      this.progress = progress;

      this.wrapperStyle.transform = null;

      if (progress < 0) {
        this.makeTransformsForStage(0);
        this.wrapperStyle.transform = "scale(0.75) translateY(25vh)";
        this.wrapperStyle.position = "absolute";
        if (-0.5 <= progress && progress < 0) {
          this.wrapperStyle.top = `calc(${-progress * 1}*20vw)`;
        }
      } else if (0 <= progress && progress <= 1) {
        const easedProgress =
          (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.wrapperStyle.transform = `scale(${
          easedProgress * 0.25 + 0.75
        }) translateY(${(1 - easedProgress) * 25}vh)`;

        this.makeTransformsForStage(easedProgress);

        this.wrapperStyle.position = "fixed";
      } else if (1 < progress && progress <= 2) {
        this.wrapperStyle.position = "fixed";
        this.wrapperStyle.top = 0;
        this.wrapperStyle.transform = `translateY(${
          (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) * rect.height * 1
        }px)`;
        this.makeTransformsForStage(1);
      } else if (2 < progress) {
        this.wrapperStyle.position = "absolute";
      }

      if (1.45 < progress && progress < 2) {
        const easedProgress =
          (Math.sin(((progress - 1.45) / (2 - 1.45)) * Math.PI - Math.PI / 2) +
            1) /
          2;
        this.styles.img1.right = `${-40.88 - easedProgress * 150}vw`;
        this.styles.img3.left = `${-97.08 - easedProgress * 150}vw`;
        this.styles.img4.right = `${4.79 - easedProgress * 250}vw`;
      } else {
        this.styles.img1.left = null;
        this.styles.img3.left = null;
        this.styles.img4.left = null;
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
  transform-origin: 50% 0;
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
    right: -40.88vw;
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
    left: -97.08vw;
    z-index: 5;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1291vw / 19.2);
    top: calc(1011vw / 19.2);
    position: absolute;
    right: 4.79vw;
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
    left: 34.04vw;
    top: 21.88vw;
    width: 63.59vw;
    z-index: 4;
    font-size: 1.9vw;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    position: absolute;
    left: 50%;
    top: 66.93vw;
    width: 69.27vw;
    transform: translateX(-51%);
    font-size: 1.9vw;
  }
}
</style>
