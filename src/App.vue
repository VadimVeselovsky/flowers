<template>
  <OpeningScreen @opened="show = true" />
  <div style="height: 10vw"></div>
  <Section7 :showAnimations="show" />
  <Section3 />
  <Section4 />
  <Section6 />
  <Section1 />
  <div style="height: 29vw"></div>
  <Section2 />
  <div style="height: 62.5vw"></div>
  <Section5 />
</template>

<script setup>
import Section1 from "@/components/objects/Section1.vue";
import Section2 from "@/components/objects/Section2.vue";
import Section3 from "@/components/objects/Section3.vue";
import Section4 from "@/components/objects/Section4.vue";
import Section5 from "@/components/objects/Section5.vue";
import Section6 from "@/components/objects/Section6.vue";
import Section7 from "@/components/objects/Section7.vue";
import OpeningScreen from "@/components/OpeningScreen.vue";
import { onMounted, ref } from "vue";

const show = ref(false);

onMounted(() => window.scroll({ left: 0 }));
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
