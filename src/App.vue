<template>
  <Section1 />
  <div style="height: 150vh"></div>
  <Section2 />
  <div style="height: 140vh"></div>
  <Section3 />
  <div style="height: 30vh"></div>
  <Section4 />
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";
import Section2 from "@/components/objects/Section2.vue";
import Section3 from "@/components/objects/Section3.vue";
import Section4 from "@/components/objects/Section4.vue";

export default {
  components: { Section1, Section2, Section3, Section4 },
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
