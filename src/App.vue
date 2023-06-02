<template>
  <div class="app">
    <div class="app__content-wrapper">
      <div class="obj">
        The action and the movements chronically blocked, through the body retroflection
        process, determine a distortion of the bodily life, the development of somatic
        tensions and inhibition, and hence the emergence of psychosomatic symptoms.
      </div>
      <div class="obj">
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
      </div>
      <!--<Object1 audio="1" style="position: absolute; left: 40%; top: 20%" />
      <Object1 audio="1" style="position: absolute; left: 50%; top: 50%" />
      <Object1 audio="krug" style="position: absolute; right: 40%; bottom: 15%" />-->
    </div>
  </div>
</template>

<script>
import Object1 from "./components/objects/Object1.vue";

export default {
  components: { Object1 },
};
</script>

<style lang="scss" scoped>
.app {
  height: 100vh;
  display: flex;
  flex-direction: column;

  &__content-wrapper {
    position: relative;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 200px 0;
  }
}
</style>

<style scoped>
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

.obj {
  width: 700px;
  height: 700px;
  font-size: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
