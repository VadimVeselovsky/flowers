<template>
  <div class="content-block-item section4">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section4__img1"
        src="@/assets/images/section4/IMG_3824.webp"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section4__img2"
        src="@/assets/images/section4/IMG_3825.avif"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section4__img3"
        src="@/assets/images/section4/IMG_3826.avif"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section4__img4"
        src="@/assets/images/section4/IMG_3827.avif"
      />
      <!--<div :style="{ transform: transforms.text }" class="section4__text2">
        he compressed and literally attacked himself<br />rather than allowing himself to
        actively express his aggressiveness outside<br /><br />he blocked the movements
        that could allow him to “push away” others making himself passive and weak.
      </div>-->
      <div :style="{ transform: transforms.text }" class="section4__text3">
        the retroflection of his need to assert himself, and of his anger<br /><br />in
        the compression of his abdominal and gastric musculature,<br /><br />and in the
        withdrawal of energy from his shoulders and arms
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

      this.show = -1 < progress && progress <= 2;

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

.section4 {
  height: 1162px;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    width: 651px;
    top: 608px;
    left: calc(50% - 1000px + 949px);
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: 990px;
    left: calc(50% - 1000px + 603px);
    top: 258px;
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 997px;
    top: 252px;
    position: absolute;
    z-index: 50;
    left: calc(50% - 1000px + 598px);
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    width: 318px;
    position: absolute;
    top: 589px;
    left: calc(50% - 1000px + 1280px);
    z-index: 2;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 239px;
    top: -209px;
    font-size: 26.5px;
    width: 712px;
    line-height: 1.3;
  }

  &__text3 {
    transform-origin: center;
    position: absolute;
    left: 448px;
    transform: translateX(-50%);
    top: 366px;
    font-size: 26.5px;
    line-height: 1.3;
  }
}
</style>
