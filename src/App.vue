<template>
  <div class="app">
    <div class="app__content-wrapper">
      <Object1 style="position: absolute; left: 40%; top: 20%" />
      <Object1 style="position: absolute; left: 50%; top: 50%" />
      <Object1 style="position: absolute; right: 40%; bottom: 15%" />
    </div>
  </div>
</template>

<script>
import Object1 from "./components/objects/Object1.vue";

export default {
  components: { Object1 },
};
</script>

<style lang="scss">
.app {
  height: 100vh;
  display: flex;
  flex-direction: column;

  &__content-wrapper {
    position: relative;
    flex-grow: 1;
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
</style>
