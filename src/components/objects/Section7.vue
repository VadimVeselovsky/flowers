<template>
  <div class="content-block-item section7">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <div class="section7__text1 text">
        we can learn a chronic and unaware way<br />
        of blocking our body expressions
      </div>
      <div class="section7__text2 text">
        the person, fearing risk and humiliation,<br />
        criticism, environment rejection,<br />
        stops and reverses the energy
      </div>
      <div class="section7__text3 text">
        the action and the movements<br />chronically blocked,<br />through the body
        retroflection process,<br /><br />determine a distortion of the bodily life
      </div>
      <div class="section7__text4 text">
        the process through which<br />the movement is inhibited and blocked<br />
        is called retroflection
      </div>
      <img class="section7__img1" src="@/assets/images/section7/13.webp" />
      <img
        @mouseenter="classes.img5 = 'section7__img5_animation'"
        @animationend="classes.img5 = null"
        :class="classes.img5"
        class="section7__img5"
        src="@/assets/images/section7/12.webp"
      />
      <img
        :style="{ transform: transforms.img6 }"
        class="section7__img6"
        src="@/assets/images/section7/11.webp"
      />
      <img
        class="section7__img7"
        src="@/assets/images/section7/14.webp"
        :style="{ transform: transforms.img7 }"
      />
      <img
        :style="{ transform: transforms.img8 }"
        class="section7__img8"
        src="@/assets/images/section7/7.webp"
      />
      <img
        :style="{ transform: transforms.img9 }"
        class="section7__img9"
        src="@/assets/images/section7/8.webp"
      />
      <img
        class="section7__img10"
        :style="{ transform: transforms.img10 }"
        src="@/assets/images/section7/9.webp"
      />

      <img
        :style="{ transform: transforms.img11 }"
        class="section7__img11"
        src="@/assets/images/section7/10.webp"
      />
    </div>
  </div>
</template>

<script>
const stepFunction = (x, step, rate) => ((Math.sin((x - step) * rate) + 1) / 2);

export default {
  data() {
    return {
      show: false,
      classes: {},
      transforms: {},
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
    makeTransformsForStage(progress) {
      progress = Math.max(Math.min(progress, 1), 0);
      progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;
      this.transforms.img10 = `translate(${17.3 * progress}vw, ${30 * progress}px)`;
      this.transforms.img7 = `translateY(${-21.6 * progress}vw)`;
      this.transforms.img4 = `translateY(${-16.6 * progress}vw)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress;

      if (!this.show) return;

      this.transforms.img9 = `scale(${stepFunction(progress, 0.02, 50) * 0.1 + 1})`;
      this.transforms.img8 = `scale(${stepFunction(progress, 0.3, 49) * 0.09 + 1})`;
      this.transforms.img6 = `scale(${stepFunction(progress, 0.32, 26) * 0.07 + 1})`;
      this.transforms.img11 = `scale(${stepFunction(progress, 0.35, 35) * 0.05 + 1})`;

      this.makeTransformsForStage((progress - 0.16) / (0.4 - 0.16));
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

@mixin enlargeOnHover($size) {
  transition: transform 0.4s;

  &:hover {
    transform: scale($size);
  }
}

@keyframes feather {
  40% {
    transform: rotate(2deg);
  }
}

.section7 {
  height: 133vw;

  &__text1 {
    position: absolute;
    left: 19vw;
    top: 6vw;
    transform: translateX(-50%);
  }

  &__text2 {
    position: absolute;
    left: 56vw;
    top: 14vw;
    transform: translateX(-50%);
  }

  &__text3 {
    position: absolute;
    left: 86vw;
    top: 53vw;
    transform: translateX(-50%);
    width: 800px;
    font-size: 25px;
  }

  &__text4 {
    position: absolute;
    left: 79vw;
    top: 117vw;
    transform: translateX(-50%);
    width: 800px;
    z-index: 100;
  }

  &__img1 {
    position: absolute;
    width: 99vw;
    left: 0;
    top: 26.2vw;
    z-index: 4;
  }

  &__img5 {
    position: absolute;
    width: 26.5vw;
    left: 10.5vw;
    top: 16.5vw;
    z-index: 40;
    transform-origin: 20% 91%;
    transform: rotate(-3deg);

    &_animation {
      animation: feather 6s;
    }
  }

  &__img6 {
    position: absolute;
    width: 20vw;
    left: 7.3vw;
    top: 47.6vw;
    z-index: 50;
  }

  &__img7 {
    position: absolute;
    width: 49vw;
    left: 28vw;
    top: 33vw;
    z-index: 2;
  }

  &__img8 {
    position: absolute;
    width: 10.6vw;
    left: 60.7vw;
    top: 65.6vw;
    z-index: 50;
  }

  &__img9 {
    position: absolute;
    width: 10vw;
    left: 86.4vw;
    top: 19vw;
    z-index: 50;
  }

  &__img10 {
    position: absolute;
    width: 93.5vw;
    right: -0.5vw;
    top: 32vw;
    z-index: 5;
  }

  &__img11 {
    position: absolute;
    width: 19.5vw;
    left: 23.5vw;
    top: 66vw;
    z-index: 50;
  }
}
</style>
