<template>
  <div class="content-block-item section1">
    <div class="wrapper" ref="wrapper">
      <img class="section1__img1" src="@/assets/images/section2/1.webp" ref="img1" />
      <video class="section1__img2" autoplay loop muted ref="img2">
        <source src="@/assets/images/section2/2.webm" type="video/webm" />
      </video>
      <video class="section1__img3" autoplay loop muted ref="img3">
        <source src="@/assets/images/section2/3.webm" type="video/webm" />
      </video>
      <video class="section1__img4" autoplay loop muted ref="img4">
        <source src="@/assets/images/section2/4.webm" type="video/webm" />
      </video>
      <div class="section1__text1" ref="text1">
        The movement is not turned on oneself, but countered by equal muscular force in
        the opposing muscle groups
      </div>
      <div class="section1__text2" ref="text2">
        In these cases the blocked action manifests itself as tension and immobility in
        the muscular groups involved.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    document.addEventListener("scroll", this.onScroll);
    this.makeTransformsForStage(0);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    makeTransformsForStage(progress) {
      if (!this.$refs.img1) return;
      this.$refs.img1.style.transform = `scale(${1 - 0.4 * (1 - progress)}) translate(-${
        (1 - progress) * 823
      }px, -${(1 - progress) * 1431}px) rotate(${50 - 13 * (1 - progress)}deg)`;
      this.$refs.img2.style.transform = `scale(${1 + 1.12 * (1 - progress)}) translate(-${
        168 * (1 - progress)
      }px, ${83 * (1 - progress)}px)`;
      this.$refs.img3.style.transform = `scale(${1 - 0.4 * (1 - progress)}) translate(${
        (1 - progress) * 946
      }px, -${(1 - progress) * 99}px) rotate(${37 - 8 * (1 - progress)}deg)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight),
        wrapper = this.$refs.wrapper;

      console.log(progress);

      if (0 <= progress && progress <= 1) {
        // progress *= 2;
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.makeTransformsForStage(progress);
        // this.$refs.text.style.transform = `translate(${-progress * 150}px, ${
        // progress * 0
        // }px) scale(${progress * 0.25 + 1})`;
        // this.$refs.img4.style.transform = `translate(${-progress * 250}px, ${
        // progress * 10
        // }px) scale(${progress * 0.35 + 1})`;
        // this.$refs.img5.style.transform = `translate(${-progress * 390}px, ${
        // progress * 200
        // }px) scale(${progress * 0.6 + 1})`;

        wrapper.style.position = "fixed";
      } else {
        if (1 < progress && progress <= 2) {
          wrapper.style.position = "fixed";
          wrapper.style.top =
            (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) *
              (rect.height - window.innerHeight) +
            "px";
          wrapper.style.bottom = "unset";
        } else {
          wrapper.style.position = "absolute";
          if (progress > 1) {
            wrapper.style.bottom = 0;
            wrapper.style.top = "unset";
          } else {
            wrapper.style.top = 0;
            wrapper.style.bottom = "unset";
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
