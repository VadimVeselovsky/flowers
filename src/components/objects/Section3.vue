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

      this.transforms.img1 = `translateY(${-progress * speed * 2500/ 19.2}vw)`;
      this.transforms.img2 = `translateY(${-progress * speed * 3000/ 19.2}vw)`;
      this.transforms.img3 = `translateY(${-progress * speed * 1300/ 19.2}vw)`;
      this.transforms.img4 = `translateY(${-progress * speed * 1100/ 19.2}vw)`;
      this.transforms.img5 = `translateY(${-progress * speed * 400/ 19.2}vw)`;
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
  height: calc(600vw/ 19.2);

  &__img1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    width: calc(888vw/ 19.2) ;
    right: calc(901vw/ 19.2);
    top: calc(492vw/ 19.2);
    z-index: 1;
  }

  &__img2 {
    transform-origin: center;
    will-change: transform;
    width: calc(331vw/ 19.2);
    right: calc(861vw/ 19.2);
    top: calc(951vw/ 19.2);
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    will-change: transform;
    width: calc(394vw/ 19.2);
    top: calc(391vw/ 19.2);
    position: absolute;
    z-index: 50;
    right: calc(154vw/ 19.2);
  }

  &__img4 {
    transform-origin: center;
    will-change: transform;
    width: calc(1773vw/ 19.2);
    position: absolute;
    top: calc(173vw/ 19.2);
    right: calc(-8vw/ 19.2);
    z-index: 15;
  }

  &__img5 {
    transform-origin: center;
    will-change: transform;
    top: calc(343vw/ 19.2);
    width: calc(959vw/ 19.2);
    right: calc(318vw/ 19.2);
    position: absolute;
    z-index: 2;
  }

  &__text1 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: calc(100vw/ 19.2);
    top: calc(93vw/ 19.2);
  }
}
</style>
