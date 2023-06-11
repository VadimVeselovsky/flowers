<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper" v-if="true || show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/section5/IMG_3842.webp"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        src="@/assets/images/section5/IMG_3843.png"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        src="@/assets/images/section5/IMG_3844.webp"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section1__img4"
        src="@/assets/images/section5/IMG_3845.webp"
      />
      <img
        :style="{ transform: transforms.img5 }"
        class="section1__img5"
        src="@/assets/images/section5/IMG_3848.webp"
      />
      <img
        :style="{ transform: transforms.img6 }"
        class="section1__img6"
        src="@/assets/images/section5/IMG_3849.webp"
      />
      <img
        :style="{ transform: transforms.img7 }"
        class="section1__img7"
        src="@/assets/images/section5/IMG_3854.webp"
      />
      <div :style="{ transform: transforms.text }" class="section1__text2">
        if he can feel accepted<br />and can finally allow himself to entrust,<br /><br /><br />
        he will then be able to unfold the blocked contact deliberateness<br /><br />
        and to gradually overcome the blocks he has put<br /><br />
        between himself and the environment
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
    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress;

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

.section1 {
  height: 100vh;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 111px;
    top: 331px;
    width: 218px;
    z-index: 3;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: 349px;
    left: 129px;
    top: -8px;
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 570px;
    top: 7px;
    position: absolute;
    z-index: 50;
    left: 1360px;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 1159px;
    top: 174px;
    width: 475px;
    z-index: 2;
  }

  &__img5 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 83px;
    width: 408px;
    top: 612px;

    z-index: 2;
  }

  &__img6 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 210px;
    width: 249px;
    top: 454px;

    z-index: 2;
  }

  &__img7 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 1223px;
    width: 673px;
    top: 262px;
    z-index: 100;
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 562px;
    top: 97px;
    font-size: 42.5px;
    width: 786px;
    line-height: 1.3;
  }
}
</style>
