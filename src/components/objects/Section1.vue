<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper">
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
      <div :style="{ transform: transforms.text }" class="section1__text">
        everything would be blocked, frozen:<br /><br />
        contact with pleasant sensations in his body was for him a source of fear
      </div>
    </div>
  </div>
</template>

<script>
// const animf1 = x =>

export default {
  data() {
    return {
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
        progress = scrollY / (rect.height - window.innerHeight);

      if (0 <= progress && progress <= 1) {
        // progress *= 2;
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.transforms.text = `translate(${-progress * 150}px, ${
          progress * 0
        }px) scale(${progress * 0.25 + 1})`;
        this.transforms.img1 = `translateX(${-progress * 50}px) scale(${
          progress * 0.3 + 1
        })`;
        this.transforms.img2 = `translate(${progress * 100}px, ${
          progress * 10
        }px) scale(${progress * 0.25 + 1})`;
        this.transforms.img3 = `translate(${progress * 540}px, ${
          progress * 70
        }px) scale(${progress * 0.6 + 1})`;
        this.transforms.img4 = `translate(${-progress * 250}px, ${
          progress * 10
        }px) scale(${progress * 0.35 + 1})`;
        this.transforms.img5 = `translate(${-progress * 390}px, ${
          progress * 200
        }px) scale(${progress * 0.6 + 1})`;

        this.wrapperStyle.position = "fixed";
      } else {
        if (1 < progress && progress <= 2) {
          this.wrapperStyle.position = "fixed";
          this.wrapperStyle.top =
            (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) *
              2 *
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
