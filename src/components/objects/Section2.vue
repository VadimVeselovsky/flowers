<template>
  <div class="content-block-item section1">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <img
        :style="{ transform: transforms.img1 }"
        class="section1__img1"
        src="@/assets/images/section2/1.webp"
      />
      <video
        :style="{ transform: transforms.img2 }"
        class="section1__img2"
        autoplay
        loop
        muted
      >
        <source src="@/assets/images/section2/2.webm" type="video/webm" />
      </video>
      <img
        :style="{ transform: transforms.img3 }"
        class="section1__img3"
        src="@/assets/images/section2/3.gif"
      />
      <video class="section1__img4" autoplay loop muted>
        <source src="@/assets/images/section2/4.webm" type="video/webm" />
      </video>
      <div class="section1__text1">
        The movement is not turned on oneself, but countered by equal muscular force in
        the opposing muscle groups
      </div>
      <div class="section1__text2">
        In these cases the blocked action manifests itself as tension and immobility in
        the muscular groups involved.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      counter: 0,
      transforms: {
        img1: null,
        img2: null,
        img3: null,
      },
      wrapperStyle: {
        transform: null,
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
      const inverse = 1 - progress;

      this.transforms.img1 = `scale(${1 - 0.2 * inverse}) translate(-${
        90 + inverse * 682
      }px, -${80 + inverse * 946}px) rotate(${53 - 14 * inverse}deg)`;
      this.transforms.img2 = `scale(${0.9 + 1.22 * inverse}) translate(-${
        14 + 156 * inverse
      }px, ${-116 + 199 * inverse}px) rotate(${5 * progress}deg)`;
      this.transforms.img3 = `scale(${1 - 0.4 * inverse}) translate(${
        23 + inverse * 925
      }px, -${59 + inverse * 40}px) rotate(${47 - 2 * inverse}deg)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / (rect.height - window.innerHeight);

      this.show = -0.5 < progress && progress <= 2.3;

      if (!this.show) return;

      if (progress < 0) this.makeTransformsForStage(0);

      /*if (progress <= 0) {
        this.wrapperStyle.transform =
          "translateY(" +
          ((1 - Math.cos(((1-progress) * 6 + 1) * Math.PI)) / 2) *
            (rect.height - window.innerHeight) +
          "px)";
      } else*/ if (
        0 <= progress &&
        progress <= 1
      ) {
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        if (this.counter++ % 4 === 0) this.makeTransformsForStage(progress);

        this.wrapperStyle.transform = null;
        this.wrapperStyle.position = "fixed";
      } else if (1 < progress && progress <= 2) {
        this.wrapperStyle.position = "fixed";
        this.wrapperStyle.top = 0;
        this.wrapperStyle.transform =
          "translateY(" +
          (-(1 - Math.cos((progress - 1) * Math.PI)) / 2) *
            (rect.height - window.innerHeight) +
          "px)";
        this.wrapperStyle.bottom = "unset";
        this.makeTransformsForStage(1);
      } else {
        this.wrapperStyle.position = "absolute";
        this.wrapperStyle.transform = null;
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
  height: 330vh;
  &__img1 {
    transform-origin: center;
    transition: transform 0.2s linear;
    width: 2000px;
    top: 2px;
    position: absolute;
    right: -786px;
    z-index: 50;
    // transform: rotate(50deg);
  }

  &__img2 {
    transform-origin: center;
    transition: transform 0.2s linear;
    width: 569px;
    top: 60px;
    position: absolute;
    right: -28px;
    z-index: 4;
  }

  &__img3 {
    transform-origin: center;
    transition: transform 0.2s linear;
    width: 4150px;
    top: -375px;
    position: absolute;
    left: -1858px;
    z-index: 5;
  }

  &__img4 {
    transform-origin: center;
    transition: transform 0.2s linear;
    width: 1291px;
    top: 1011px;
    position: absolute;
    right: 92px;
    z-index: 50;
    transform: rotate(3deg);
  }

  &__img5 {
    transform-origin: center;
    transition: transform 0.2s linear;
    width: 500px;
    bottom: -110px;
    left: 0;
    position: absolute;
    z-index: 2;
  }

  &__text1 {
    transform-origin: center;
    transition: transform 0.2s linear;
    position: absolute;
    left: calc(42% - 300px);
    top: 328px;
    font-size: 51px;
    width: 1221px;
    z-index: 4;
  }

  &__text2 {
    transform-origin: center;
    transition: transform 0.2s linear;
    position: absolute;
    left: 87px;
    top: 1315px;
    font-size: 51px;
    width: 1330px;
  }
}
</style>
