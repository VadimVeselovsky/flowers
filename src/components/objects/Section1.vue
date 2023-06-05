<template>
  <div class="content-block-item section1">
    <img class="section1__img1" src="@/assets/images/IMG_1599.png" />
    <div class="section1__text">
      everything would be blocked, frozen:<br /><br />
      contact with pleasant sensations in his body was for him a source of fear
    </div>
  </div>
</template>

<style lang="scss" scoped>
// this.$refs.qwe.style.transform = `translate(-${
// animationStage * 100
// }px, ${scrollTop}px) scale(${animationStage * 1 + 1})`;
.section1 {
  &__img1 {
    width: 1200px;
    top: calc(-50% + 450px);
    transform: translate(0, calc(var(--scroll-progress) * 3 * 200vh))
      scale(calc(var(--scroll-progress) * 3 * 0.5 + 1));
  }

  &__text {
    position: absolute;
    left: 50%;
    top: 12%;
    font-size: 25px;
    transform: translate(
        calc(var(--scroll-progress) * 3 * (-150px)),
        calc(var(--scroll-progress) * 3 * 200vh)
      )
      scale(calc(var(--scroll-progress) * 3 + 1));
  }
}
</style>
