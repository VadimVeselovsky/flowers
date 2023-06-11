<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper" v-show="show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/section3/IMG_3829.png"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        src="@/assets/images/section3/IMG_3832.png"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        src="@/assets/images/section3/IMG_3833.png"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section1__img4"
        src="@/assets/images/section3/IMG_3834.png"
      />
      <img
        :style="{ transform: transforms.img5 }"
        class="section1__img5"
        src="@/assets/images/section3/IMG_3835.png"
      />
      <video class="section1__img6" autoplay loop muted>
        <source src="@/assets/images/section3/animation.webm" type="video/webm" />
      </video>
      <div :style="{ transform: transforms.text }" class="section1__text1">
        The first form of retroflection is the literal reversal onto oneself of the action
        one wants to do to the environment.
      </div>
      <div :style="{ transform: transforms.text }" class="section1__text2">
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
  height: 370vh;

  &__img1 {
    transform-origin: center;
    position: absolute;
    width: 1843px;
    left: 64px;
    top: -101px;
  }

  &__img2 {
    transform-origin: center;
    width: 1855px;
    left: 56px;
    top: -107px;
    position: absolute;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    width: 1869px;
    top: -111px;
    position: absolute;
    z-index: 50;
    right: -8px;
  }

  &__img4 {
    transform-origin: center;
    width: 1787px;
    position: absolute;
    top: -98px;
    left: 112px;
    z-index: 2;
  }

  &__img5 {
    transform-origin: center;
    top: -102px;
    width: 1841px;
    left: 65px;
    position: absolute;
    z-index: 2;
  }

  &__img6 {
    position: absolute;
    top: 373px;
    left: -485px;
    width: 3928px;
  }

  &__text1 {
    transform-origin: center;
    position: absolute;
    left: 100px;
    top: 93px;
    font-size: 32px;
    width: 810px;
    line-height: 1.36;
  }

  &__text2 {
    transform-origin: center;
    position: absolute;
    left: 1024px;
    top: 1099px;
    font-size: 32px;
    width: 652px;
    line-height: 1.36;
  }
}
</style>
