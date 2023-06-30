<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <Teleport to="#indicators">
        <div style="left: 16rem">5: {{ (progress * 100).toFixed(0) }}</div>
      </Teleport>
      <div class="section1__pre-block pre-block">
        <img
          :style="{ transform: transforms.preimg1 }"
          class="pre-block__img1"
          src="@/assets/images/section1/IMG_1748.webp"
        />
        <img
          :style="{ transform: transforms.preimg2 }"
          class="pre-block__img2"
          src="@/assets/images/section1/IMG_1749.webp"
        />
      </div>
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/IMG_1599.webp"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        src="@/assets/images/IMG_1598.webp"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        src="@/assets/images/IMG_1608.webp"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section1__img4"
        src="@/assets/images/IMG_1610.webp"
      />
      <img
        :style="{ transform: transforms.img5 }"
        class="section1__img5"
        src="@/assets/images/IMG_1611.webp"
      />
      <div :style="{ transform: transforms.text }" class="section1__text text">
        everything would be blocked, frozen:<br />
        contact with pleasant sensations in his body was for him a source of
        fear
      </div>
    </div>
  </div>
</template>

<script>
// const animf1 = x =>

export default {
  data() {
    return {
      progress: 0,
      show: true,
      counter: 0,
      transforms: {},
      wrapperStyle: {
        top: null,
        bottom: null,
        position: null,
      },
    };
  },

  mounted() {
    this.onScroll();
    document.addEventListener("scroll", this.onScroll);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    makeTransformsForStage(progress) {
      this.transforms.text = `translateX(${(-progress * 150) / 19.2}vw) scale(${
        progress * 0.2 + 0.8
      })`;
      this.transforms.img1 = `translateX(${(-progress * 50) / 19.2}vw) scale(${
        progress * 0.3 + 1
      })`;
      this.transforms.img2 = `translate(${(progress * 100) / 19.2}vw, ${
        (progress * 10) / 19.2
      }vw) scale(${progress * 0.25 + 1})`;
      this.transforms.img3 = `translate(${(progress * 540) / 19.2}vw, ${
        (progress * 70) / 19.2
      }vw) scale(${progress * 0.6 + 1})`;
      this.transforms.img4 = `translate(${(-progress * 250) / 19.2}vw, ${
        (progress * 10) / 19.2
      }vw) scale(${progress * 0.35 + 1})`;
      this.transforms.img5 = `translate(${(-progress * 390) / 19.2}vw, ${
        (progress * 200) / 19.2
      }vw) scale(${progress * 0.6 + 1})`;

      this.transforms.preimg2 = `scaleY(${1 - progress})`;
    },

    onScroll() {
      const hideOn = 3;

      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -1.5 < progress && progress <= hideOn;

      if (!this.show) return;

      this.progress = progress;

      console.log(progress);

      if (progress < 0) {
        this.makeTransformsForStage(0);
      }

      if (0 <= progress && progress <= 1) {
        progress =
          (progress < 0.8
            ? (Math.sin((progress / 0.8) * Math.PI - Math.PI / 2) + 1) / 2
            : 1) +
          (Math.log(progress + 5) - Math.log(5));

        if (this.counter++ % 4 === 0) this.makeTransformsForStage(progress);

        this.wrapperStyle.position = "fixed";
        this.wrapperStyle.transform = null;
      } else if (1 < progress && progress <= 2) {
        this.wrapperStyle.position = "fixed";
        this.wrapperStyle.top = 0;
        this.wrapperStyle.transform =
          "translateY(" +
          (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) * rect.height +
          "px)";
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

.section1 {
  height: calc(3800vw / 19.2);

  &__pre-block {
    bottom: calc(100% - 52.1vw);
    width: 100%;
    z-index: 100;
  }

  &__img1 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1081vw / 19.2);
    top: calc(-135vw / 19.2);
    position: absolute;
    left: calc(361vw / 19.2);
    z-index: 2;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1141vw / 19.2);
    top: calc(-120vw / 19.2);
    position: absolute;
    right: 0;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1141vw / 19.2);
    top: calc(-120vw / 19.2);
    position: absolute;
    right: 0;
    z-index: 50;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(1141vw / 19.2);
    position: absolute;
    left: calc(-219vw / 19.2);
    top: calc(-456vw / 19.2);
    z-index: 2;
  }

  &__img5 {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    width: calc(500vw / 19.2);
    top: calc(451vw / 19.2);
    left: 0;
    position: absolute;
    z-index: 2;
  }

  &__text {
    transform-origin: center;
    will-change: transform;
    transition: transform 0.2s linear;
    position: absolute;
    left: calc(947vw / 19.2);
    top: calc(273vw / 19.2);
  }
}

.pre-block {
  position: absolute;
  height: calc(100vw / 19.2);

  &__img1 {
    width: 100%;
    position: absolute;
    bottom: 0;
  }
  &__img2 {
    width: 100%;
    position: absolute;
    bottom: 0;
  }
}
</style>
