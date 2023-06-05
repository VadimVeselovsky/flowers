<template>
  <div class="content-block-item section1">
    <img class="section1__img1" src="@/assets/images/IMG_1599.png" ref="img1" />
    <img class="section1__img2" src="@/assets/images/IMG_1598.png" ref="img2" />
    <img class="section1__img3" src="@/assets/images/IMG_1596.png" ref="img3" />
    <div class="section1__text" ref="text">
      everything would be blocked, frozen:<br /><br />
      contact with pleasant sensations in his body was for him a source of fear
    </div>
  </div>
</template>

<script>
export default {
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

      if (progress < 1) {
        progress = (Math.sin(progress * Math.PI - Math.PI / 2) + 1) / 2;

        this.$refs.text.style.transform = `translate(${
          -progress * 170
        }px, ${scrollY}px) scale(${progress * 0.5 + 1})`;

        this.$refs.img1.style.transform = `translate(${
          -progress * 50
        }px, ${scrollY}px) scale(${progress * 0.3 + 1})`;
        this.$refs.img2.style.transform = `translate(${progress * 70}px, ${
          scrollY + progress * 25
        }px) scale(${progress * 0.25 + 1})`;
        this.$refs.img3.style.transform = `translate(${progress * 140}px, ${
          scrollY + progress * 70
        }px) scale(${progress * 0.5 + 1})`;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.section1 {
  height: 100vh;

  &__img1 {
    transform-origin: center;
    width: 1141px;
    top: -221px;
    position: absolute;
    left: 0;
    z-index: 2;
  }

  &__img2 {
    transform-origin: center;
    width: 1141px;
    top: -260px;
    position: absolute;
    right: 0;
    z-index: 2;
  }

  &__img3 {
    transform-origin: center;
    width: 1141px;
    top: -73px;
    position: absolute;
    right: 0;
    z-index: 2;
  }

  &__text {
    transform-origin: center;
    position: absolute;
    left: 40%;
    top: 45%;
    font-size: 25px;
  }
}
</style>
