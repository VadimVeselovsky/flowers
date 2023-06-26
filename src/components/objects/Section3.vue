<template>
  <div class="content-block-item section3">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section3__img1"
        src="@/assets/images/section3/1.avif"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section3__img2"
        src="@/assets/images/section3/2.avif"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section3__img3"
        src="@/assets/images/section3/3.avif"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section3__img4"
        src="@/assets/images/section3/4.webp"
      />
      <img
        :style="{ transform: transforms.img5 }"
        class="section3__img5"
        src="@/assets/images/section3/5.avif"
      />
      <div :style="{ transform: transforms.text }" class="section3__text1 text">
        The first form of retroflection is the literal reversal onto oneself<br />
        of the action one wants to do to the environment.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true,
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
    makeTransformsForStage(progress) {
      const speed = 0.35;

      this.transforms.img1 = `translateY(${-progress * speed * 2500}px)`;
      this.transforms.img2 = `translateY(${-progress * speed * 3000}px)`;
      this.transforms.img3 = `translateY(${-progress * speed * 1300}px)`;
      this.transforms.img4 = `translateY(${-progress * speed * 1100}px)`;
      this.transforms.img5 = `translateY(${-progress * speed * 400}px)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress && progress <= 2;

      if (!this.show) return;

      this.makeTransformsForStage(progress);
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

.section3 {
  height: 600px;

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    width: 888px;
    right: 901px;
    top: calc(392px + 100px);
    z-index: 1;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: 331px;
    right: 861px;
    top: calc(851px + 100px);
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: 394px;
    top: calc(291px + 100px);
    position: absolute;
    z-index: 50;
    right: 154px;
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    width: 1773px;
    position: absolute;
    top: calc(73px + 100px);
    right: -8px;
    z-index: 15;
  }

  &__img5 {
    transform-origin: center;
    will-change: transform;
    top: calc(243px + 100px);
    width: 959px;
    right: 318px;
    position: absolute;
    z-index: 2;
  }

  &__text1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 100px;
    top: 93px;
  }
}
</style>
