<template>
  <div class="content-block-item section7">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <Teleport to="#indicators">
        <div>1</div>
      </Teleport>
      <div
        class="section7__text1 text"
        :class="{ section7__text1_animated: showAnimations }"
        :style="styles.text1"
      >
        we can learn a chronic and unaware way<br />
        of blocking our body expressions
      </div>
      <div
        class="section7__text2 text"
        :class="{ section7__text2_animated: showAnimations }"
        :style="styles.text2"
      >
        the person, fearing risk and humiliation,<br />
        criticism, environment rejection,<br />
        stops and reverses the energy
      </div>
      <div class="section7__text3 text">
        the action and the movements<br />chronically blocked<br /><br />determine
        a distortion of the bodily life
      </div>
      <div
        class="section7__text4 text"
        :class="{ section7__text4_animate: progress > 0.5 }"
      >
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
        class="section7__img6"
        :class="{ section7__img6_animated: progress > 0.22 }"
        src="@/assets/images/section7/11.webp"
      />
      <img
        class="section7__img7"
        src="@/assets/images/section7/14.webp"
        :style="{ transform: transforms.img7 }"
      />
      <img
        class="section7__img8"
        :class="{ section7__img8_animated: progress > 0.22 }"
        src="@/assets/images/section7/7.webp"
      />
      <img class="section7__img9" src="@/assets/images/section7/8.webp" />
      <img
        class="section7__img10"
        :style="{ transform: transforms.img10 }"
        src="@/assets/images/section7/9.webp"
      />

      <img
        class="section7__img11"
        :class="{ section7__img11_animated: progress > 0.22 }"
        src="@/assets/images/section7/10.webp"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    showAnimations: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      progress: 0,
      show: false,
      classes: {},
      transforms: {},
      styles: {},
      wrapperStyle: {},
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
      this.transforms.img10 = `translate(${17.3 * progress}vw, ${
        1.6 * progress
      }vw)`;
      this.transforms.img7 = `translateY(${-22.6 * progress}vw)`;
      this.transforms.img4 = `translateY(${-16.6 * progress}vw)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress && progress < 1.2;

      if (!this.show) return;

      this.progress = progress;

      this.wrapperStyle.transform = `translateY(${progress * 100}vw)`;

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

@keyframes fade-in {
  to {
    opacity: 1;
  }
}

@keyframes fade-in-out {
  15%,
  95% {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

@keyframes booping {
  50% {
    transform: scale(1.07);
  }
}

@keyframes booping_small {
  50% {
    transform: scale(1.04);
  }
}

@keyframes booping_small1 {
  50% {
    transform: scale(1.055);
  }
}

@keyframes space_floating {
  from,
  to {
    transform: rotate(-35deg);
  }

  50% {
    transform: rotate(-41deg);
  }
}

.section7 {
  height: 233vw;

  &__text1 {
    position: absolute;
    left: 23vw;
    top: 4vw;
    transform: translateX(-50%);
    opacity: 0;
    &_animated {
      animation: 1s ease 1s fade-in;
      animation-fill-mode: forwards;
    }
  }

  &__text2 {
    position: absolute;
    left: 56vw;
    top: 12vw;
    transform: translateX(-50%);
    opacity: 0;
    &_animated {
      animation: 1s ease 2.8s fade-in;
      animation-fill-mode: forwards;
    }
  }

  &__text3 {
    position: absolute;
    left: 86vw;
    top: 53vw;
    transform: translateX(-50%);
    width: 41.6vw;
    font-size: 1.3vw;
  }

  &__text4 {
    position: absolute;
    left: 79vw;
    top: 121vw;
    transform: translateX(-50%);
    width: 41.6vw;
    z-index: 100;
    opacity: 0;
    transition: opacity 1s;

    &_animate {
      animation: 10s ease 0.5s fade-in-out;
      animation-fill-mode: forwards;
    }
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

    &_animated {
      animation: 7s ease 2s booping_small;
      animation-iteration-count: infinite;
    }
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

    &_animated {
      animation: 7s ease booping_small1;
      animation-iteration-count: infinite;
    }
  }

  &__img9 {
    position: absolute;
    width: 10vw;
    left: 86.4vw;
    top: 19vw;
    z-index: 50;
    transform-origin: 0% 100%;
    animation: 13s ease-in-out 0 space_floating;
    animation-iteration-count: infinite;
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

    &_animated {
      animation: 7s ease 4s booping;
      animation-iteration-count: infinite;
    }
  }
}
</style>
