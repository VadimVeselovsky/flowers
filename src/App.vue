<template>
  <Section1 />
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";

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
  margin: 0 auto;

  &-item {
    position: relative;
    font-size: 45px;
    line-height: 1.25;
    letter-spacing: 0.5px;
  }
}
</style>
