<template>
  <div :class="{ 'zero-height': !show }">
    <OpeningScreen @opened="(show = true), scrollToTop()" />
    <div style="height: 10vw"></div>
    <Section7 :isActive="show" />
    <Section3 />
    <Section4 />
    <Section6 />
    <Section1 />
    <div style="height: 100vw"></div>
    <Section2 />
    <div style="height: 130vw"></div>
    <Section5 />
  </div>
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

function scrollToTop() {
  window.scroll({ left: 0, top: 0 });
}

onMounted(scrollToTop);

onMounted(() => {
  if (location.host.startsWith("localhost"))
    document.getElementById("indicators").style.display = "flex";
});
</script>

<style lang="scss">
.content-block {
  &-item {
    position: relative;
  }
}
.zero-height {
  height: 0;
}
</style>
