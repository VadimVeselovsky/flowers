<template>
  <div class="content-block-item section1">
    <div class="wrapper" ref="wrapper">
      <img class="section1__img1" src="@/assets/images/IMG_1599.webp" ref="img1" />
      <img class="section1__img2" src="@/assets/images/IMG_1598.webp" ref="img2" />
      <img class="section1__img3" src="@/assets/images/IMG_1608.webp" ref="img3" />
      <img class="section1__img4" src="@/assets/images/IMG_1610.webp" ref="img4" />
      <img class="section1__img5" src="@/assets/images/IMG_1611.webp" ref="img5" />
      <div class="section1__text" ref="text">
        everything would be blocked, frozen:<br /><br />
        contact with pleasant sensations in his body was for him a source of fear
      </div>
    </div>
  </div>
</template>

<script>
// const animf1 = x =>

export default {
  mounted() {
    this.onScroll();
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

        this.$refs.text.style.transform = `translate(${-progress * 150}px, ${
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
        }px) scale(${progress * 0.6 + 1})`;

        wrapper.style.position = "fixed";
      } else {
        if (1 < progress && progress <= 2) {
          wrapper.style.position = "fixed";
          wrapper.style.top =
            (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) *
              2 *
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
  z-index: 100;
}

.section1 {
  height: 700vh;

  &__img1 {
    transform-origin: center;
    width: 1081px;
    top: -135px;
    position: absolute;
    left: 361px;
    z-index: 2;
  }

  &__img2 {
    transform-origin: center;
    width: 1141px;
    top: -120px;
    position: absolute;
    right: 0;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    width: 1141px;
    top: -120px;
    position: absolute;
    right: 0;
    z-index: 50;
  }

  &__img4 {
    transform-origin: center;
    width: 1141px;
    position: absolute;
    left: -219px;
    top: -456px;
    z-index: 2;
  }

  &__img5 {
    transform-origin: center;
    width: 500px;
    bottom: -110px;
    left: 0;
    position: absolute;
    z-index: 2;
  }

  &__text {
    transform-origin: center;
    position: absolute;
    left: calc(66% - 300px);
    top: calc(33% + 3px);
    font-size: 25px;
  }
}
</style>
