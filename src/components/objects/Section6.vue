<template>
  <div class="content-block-item section6">
    <div :style="wrapperStyle" class="wrapper" v-if="show">
      <video class="section6__img6" autoplay loop muted>
        <source src="@/assets/images/section6/animation.webm" type="video/webm" />
      </video>

      <div :style="{ transform: transforms.text }" class="section6__text2">
        the act of compressing himself<br />
        kept on functioning as a physical symptom
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

.section6 {
  height: 3420px;
  overflow: hidden;

  &__img6 {
    position: absolute;
    top: -200px;
    left: calc(50% + 530px);
    width: 3928px;
    transform: translateX(-50%);
  }

  &__text2 {
    transform-origin: center;
    will-change: transform;
    position: absolute;
    left: 50%;
    top: 410px;
    font-size: 32px;
    width: 898px;
    line-height: 1.36;
  }
}
</style>
