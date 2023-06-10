<template>
  <div class="content-block-item section1">
    <img src="@/assets/images/section2/4.gif" />
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
// const animf1 = x =>

export default {
  mounted() {
    document.addEventListener("scroll", this.onScroll);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight),
        wrapper = this.$refs.wrapper;

      if (0 <= progress && progress <= 1) {
        // progress *= 2;
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        /*this.$refs.text.style.transform = `translate(${-progress * 150}px, ${
          progress * 0
        }px) scale(${progress * 0.25 + 1})`;
        this.$refs.img1.style.transform = `translateX(${-progress * 50}px) scale(${
          progress * 0.3 + 1
        })`;
        this.$refs.img2.style.transform = `translate(${progress * 100}px, ${
          progress * 10
        }px) scale(${progress * 0.25 + 1})`;
        this.$refs.img3.style.transform = `translate(${progress * 540}px, ${
          progress * 70
        }px) scale(${progress * 0.6 + 1})`;
        this.$refs.img4.style.transform = `translate(${-progress * 250}px, ${
          progress * 10
        }px) scale(${progress * 0.35 + 1})`;
        this.$refs.img5.style.transform = `translate(${-progress * 390}px, ${
          progress * 200
        }px) scale(${progress * 0.6 + 1})`;*/

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
  height: 100%;

  &__img1 {
    transform-origin: center;
    width: 2000px;
    top: -398px;
    position: absolute;
    right: -786px;
    z-index: 5;
    transform: rotate(50deg);
  }

  &__img2 {
    transform-origin: center;
    width: 569px;
    top: -340px;
    position: absolute;
    right: -28px;
    z-index: 4;
  }

  &__img3 {
    transform-origin: center;
    width: 4200px;
    top: -2047px;
    position: absolute;
    left: -2530px;
    z-index: 0;
    transform: rotate(47deg);
  }

  &__img4 {
    transform-origin: center;
    width: 1226px;
    top: 715px;
    position: absolute;
    right: 123px;
    z-index: 50;
    transform: rotate(3deg);
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
    top: 23px;
    font-size: 51px;
    width: 1221px;
    z-index: 10;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 80px;
    top: 1007px;
    font-size: 51px;
    width: 1330px;
  }
}
</style>
