<template>
  <div class="app">
    <div class="app__content-wrapper">
      <div class="content-block">
        <Section1 />

        <!--<div class="content-block__item" style="left: 30%; top: 15%; width: 55%">
        we can learn a chronic and unaware way of blocking our body expressions,<br /><br />the
        movements that could potentially give a full form to the communication of our
        needs
        </div>
        
        <div class="content-block__item" style="left: 62%; top: 63%; width: 37%">
        The process through which the movement is inhibited and blocked is called
        retroflection.
        </div>
        <div class="content-block__item" style="left: 2%; top: 66%; width: 41%">
        The person, fearing risk and humiliation, criticism, environment rejection,
        stops and reverses the energy
        </div>-->
      </div>
      <!--<div class="obj">
        The first form of retroflection is the literal reversal onto oneself of the action
        one wants to do to the environment
      </div>
      <div class="obj">
        The retroflection of his need to assert himself, and of his anger for not feeling
        respected, found its somatic correlate in the compression of his abdominal and
        gastric musculature, and in the withdrawal of energy from his shoulders and arms.
      </div>
      <div class="obj">
        He compressed and literally attacked himself rather than allowing himself to
        actively express his aggressiveness outside,<br /><br />he blocked the movements
        that could allow him to “push away” others or to keep them at the right distance,
        making himself passive and weak.<br /><br />The act of compressing himself, kept
        outside of his awareness, had kept on functioning as a physical symptom.
      </div>
      <div class="obj">
        The second form of retroflective behaviour happens when the movement directed
        towards the environment is physically inhibited as soon as it starts.<br /><br />The
        movement is not turned on oneself, but “countered by equal muscular force in the
        opposing muscle groups” (Kepner, 1993, 148). In these cases the blocked action
        manifests itself as tension and immobility in the muscular groups involved.
      </div>
      <div class="obj">
        recognizing the fact that his destructive hate and his renunciation to feed
        himself were instead part of a passive and weak attitude that he had put on in the
        face of reality, also with a secret hope that he could have been seen and
        therefore helped
      </div>
      <div class="obj">
        if he can feel accepted and can finally allow himself to entrust himself, <br />
        <br />
        he will then be able to unfold the blocked contact deliberateness <br />
        <br />
        and to gradually overcome<br />
        <br />
        the blocks he has put<br />
        <br />
        between himself and the environment
      </div>-->
    </div>
  </div>
</template>

<script>
import Section1 from "@/components/objects/Section1.vue";

export default {
  components: { Section1 },

  mounted() {
    document.addEventListener("scroll", this.onScroll);
  },

  beforeDestroy() {
    document.removeEventListener("scroll", this.onScroll);
  },

  methods: {
    onScroll() {
      const scrollTop = window.scrollY,
        screenHeight = document.body.clientHeight,
        animationStage = scrollTop / (document.body.scrollHeight - screenHeight);
      document.querySelector(":root").style.setProperty("--scroll", animationStage);
      // this.$refs.qwe.style.transform = `translate(-${
      // animationStage * 100
      // }px, ${scrollTop}px) scale(${animationStage * 1 + 1})`;
    },
  },
};
</script>

<style lang="scss">
.app {
  display: flex;
  flex-direction: column;

  &__content-wrapper {
    position: relative;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}

.content-block {
  height: 102vh;
  width: 90%;
  margin: 0 auto;
  position: relative;

  &__item {
    position: absolute;
    font-size: 45px;
    line-height: 1.25;
    letter-spacing: 0.5px;
  }
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
