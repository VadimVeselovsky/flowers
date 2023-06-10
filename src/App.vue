<template>
  <Section1 />
  <div style="height: 150vh"></div>
  <Section2 />
  <div style="height: 250vh"></div>
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";
import Section2 from "@/components/objects/Section2.vue";

export default {
  components: { Section1, Section2 },

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
