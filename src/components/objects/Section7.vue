<template>
  <div class="content-block-item section7">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <div class="section7__text1 text">
        we can learn a chronic and unaware way<br />
        of blocking our body expressions
      </div>
      <div class="section7__text2 text">
        the person, fearing risk and humiliation,<br />
        criticism, environment rejection,<br /><br />
        stops and reverses the energy
      </div>
      <div class="section7__text3 text">
        the action and the movements<br />chronically blocked,<br />through the body
        retroflection process,<br /><br />determine a distortion of the bodily life
      </div>
      <div class="section7__text4 text">
        the process through which the movement<br />
        is inhibited and blocked<br />
        is called retroflection
      </div>
      <img
        :style="{ transform: transforms.img1 }"
        class="section7__img1"
        src="@/assets/images/section7/IMG_1760.avif"
      />
      <img
        :style="{ transform: transforms.img2 }"
        class="section7__img2"
        src="@/assets/images/section7/IMG_1761.avif"
      />
      <img
        :style="{ transform: transforms.img3 }"
        class="section7__img3"
        src="@/assets/images/section7/IMG_1762.avif"
      />
      <img
        :style="{ transform: transforms.img4 }"
        class="section7__img4"
        src="@/assets/images/section7/IMG_1763.avif"
      />
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
      this.transforms.img2 = `translate(${10.9 * progress}vw, ${30 * progress}px)`;
      this.transforms.img3 = `translateY(${-21.6 * progress}vw)`;
      this.transforms.img4 = `translateY(${-16.6 * progress}vw)`;
    },

    onScroll() {
      let rect = this.$el.getBoundingClientRect(),
        scrollY =
          window.scrollY -
          (rect.y - document.getElementById("app").getBoundingClientRect().y),
        progress = scrollY / rect.height;

      this.show = -2 < progress;

      console.log(progress);

      if (!this.show) return;

      this.makeTransformsForStage((progress - 0.23) / (0.3 - 0.2));
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

.section7 {
  height: 145vw;

  &__text1 {
    position: absolute;
    left: 19vw;
    top: 6vw;
    transform: translateX(-50%);
  }

  &__text2 {
    position: absolute;
    left: 53vw;
    top: 20vw;
    transform: translateX(-50%);
  }

  &__text3 {
    position: absolute;
    left: 86vw;
    top: 53vw;
    transform: translateX(-50%);
    width: 800px;
  }

  &__text4 {
    position: absolute;
    left: 70vw;
    top: 120vw;
    transform: translateX(-50%);
    width: 800px;
    z-index: 100;
  }

  &__img1 {
    position: absolute;
    width: 99vw;
    left: 0;
    top: 2.5vw;
    z-index: 4;
  }

  &__img2 {
    position: absolute;
    width: 100vw;
    right: 0vw;
    top: -2vw;
  }

  &__img3 {
    position: absolute;
    width: 105vw;
    left: -3vw;
    top: -1.8vw;

    &_open {
      transform: translate(-5%, -5%);
    }
  }

  &__img4 {
    position: absolute;
    width: 99vw;
    left: 0;
    top: 25.5vw;
    z-index: 4;
  }

  &__img5 {
    position: absolute;
    width: 96vw;
    right: 0;
    top: 32.5vw;

    &_open {
      transform: translate(16%, 5%);
    }
  }

  &__img6 {
    position: absolute;
    width: 35vw;
    right: 17vw;
    top: 39.5vw;

    &_open {
      transform: translate(-20%, -7%);
    }
  }
}
</style>
