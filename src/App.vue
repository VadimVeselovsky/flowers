<template>
  <div style="height: 15vh"></div>
  <Section7 />
  <Section3 />
  <Section4 />
  <Section6 />
  <Section1 />
  <div style="height: 80vh"></div>
  <Section2 />
  <div style="height: 941px"></div>
  <Section5 />
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";
import Section2 from "@/components/objects/Section2.vue";
import Section3 from "@/components/objects/Section3.vue";
import Section4 from "@/components/objects/Section4.vue";
import Section5 from "@/components/objects/Section5.vue";
import Section6 from "@/components/objects/Section6.vue";
import Section7 from "@/components/objects/Section7.vue";

export default {
  components: {
    Section1,
    Section2,
    Section3,
    Section4,
    Section5,
    Section6,
    Section7,
  },

  mounted() {
    window.scroll({ left: 0 });
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
