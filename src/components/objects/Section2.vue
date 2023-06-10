<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper">
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/section2/1.webp"
      />
      <video
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/2.webm" type="video/webm" />
      </video>
      <video
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/3.webm" type="video/webm" />
      </video>
      <video class="section1__img4" autoplay loop muted>
        <source src="@/assets/images/section2/4.webm" type="video/webm" />
      </video>
      <div class="section1__text1">
        The movement is not turned on oneself, but countered by equal muscular force in
        the opposing muscle groups
      </div>
      <div class="section1__text2">
        In these cases the blocked action manifests itself as tension and immobility in
        the muscular groups involved.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      transforms: {
        img1: null,
        img2: null,
        img3: null,
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
    this.makeTransformsForStage(0);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    makeTransformsForStage(progress) {
      this.transforms.img1 = `scale(${1 - 0.4 * (1 - progress)}) translate(-${
        (1 - progress) * 823
      }px, -${(1 - progress) * 1431}px) rotate(${50 - 13 * (1 - progress)}deg)`;
      this.transforms.img2 = `scale(${1 + 1.12 * (1 - progress)}) translate(-${
        168 * (1 - progress)
      }px, ${83 * (1 - progress)}px)`;
      this.transforms.img3 = `scale(${1 - 0.4 * (1 - progress)}) translate(${
        (1 - progress) * 946
      }px, -${(1 - progress) * 99}px) rotate(${37 - 8 * (1 - progress)}deg)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight);

      console.log(progress);

      if (0 <= progress && progress <= 1) {
        // progress *= 2;
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.makeTransformsForStage(progress);

        this.wrapperStyle.position = "fixed";
      } else {
        if (1 < progress && progress <= 2) {
          this.wrapperStyle.position = "fixed";
          this.wrapperStyle.top =
            (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) *
              (rect.height - window.innerHeight) +
            "px";
          this.wrapperStyle.bottom = "unset";
        } else {
          this.wrapperStyle.position = "absolute";
          if (progress > 1) {
            this.wrapperStyle.bottom = 0;
            this.wrapperStyle.top = "unset";
          } else {
            this.wrapperStyle.top = 0;
            this.wrapperStyle.bottom = "unset";
          }
        }
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

.section1 {
  height: 600vh;
  &__img1 {
    transform-origin: center;
    width: 2000px;
    top: 2px;
    position: absolute;
    right: -786px;
    z-index: 5;
    // transform: rotate(50deg);
  }

  &__img2 {
    transform-origin: center;
    width: 569px;
    top: 60px;
    position: absolute;
    right: -28px;
    z-index: 4;
  }

  &__img3 {
    transform-origin: center;
    width: 4200px;
    top: -375px;
    position: absolute;
    left: -1858px;
    z-index: 5;
    // transform: rotate(37deg);
  }

  &__img4 {
    transform-origin: center;
    width: 1226px;
    top: 1115px;
    position: absolute;
    right: 123px;
    z-index: 50;
    // transform: rotate(3deg);
  }

  &__img5 {
    transform-origin: center;
    width: 500px;
    bottom: -110px;
    left: 0;
    position: absolute;
    z-index: 2;
  }

  &__text1 {
    transform-origin: center;
    position: absolute;
    left: calc(42% - 300px);
    top: 423px;
    font-size: 51px;
    width: 1221px;
    z-index: 3;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 153px;
    top: 1431px;
    font-size: 51px;
    width: 1330px;
  }
}
</style>
