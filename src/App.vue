<template>
  <div class="content-block">
    <Section1 />
  </div>
  <div class="content-block" style="background: red"></div>
  <div class="content-block"></div>
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";

const numberOfSections = 3;

export default {
  components: { Section1 },

  mounted() {
    document.addEventListener("scroll", this.updateAnimationProgress);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.updateAnimationProgress);
  },

  methods: {
    updateAnimationProgress() {
      const scrollTop = window.scrollY,
        screenHeight = window.innerHeight,
        animationProgress = scrollTop / (document.body.scrollHeight - screenHeight);
      document
        .querySelector(":root")
        .style.setProperty("--scroll-progress", animationProgress);
    },
  },
};
</script>

<style lang="scss">
.content-block {
  height: 200vh;
  margin: 0 auto;
  position: relative;

  &-item {
    font-size: 45px;
    line-height: 1.25;
    letter-spacing: 0.5px;
    height: 100%;
  }
}
</style>
