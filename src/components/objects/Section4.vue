<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/section4/IMG_3824.webp"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        src="@/assets/images/section4/IMG_3825.png"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        src="@/assets/images/section4/IMG_3826.png"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section1__img4"
        src="@/assets/images/section4/IMG_3827.png"
      />
      <div :style="{ transform: transforms.text }" class="section1__text2">
        he compressed and literally attacked himself<br />rather than allowing himself to
        actively express his aggressiveness outside<br /><br />he blocked the movements
        that could allow him to “push away” others making himself passive and weak.
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
        progress = scrollY / (rect.height - window.innerHeight);

      this.show = -0.4 < progress && progress <= 2;

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
    position: absolute;
    width: 651px;
    top: 208px;
    left: 1149px;
  }

  &__img2 {
    transform-origin: center;
    width: 990px;
    left: 803px;
    top: -142px;
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    width: 997px;
    top: -148px;
    position: absolute;
    z-index: 50;
    left: 798px;
  }

  &__img4 {
    transform-origin: center;
    width: 318px;
    position: absolute;
    top: 189px;
    left: 1480px;
    z-index: 2;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 1249px;
    top: 305px;
    font-size: 26.5px;
    width: 512px;
    line-height: 1.3;
  }
}
</style>
