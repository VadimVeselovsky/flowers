<template>
  <div
    @animationend="deactivate"
    class="object"
    :class="{
      object_activated: isActivated,
    }"
  >
    <audio preload ref="audio">
      <source :src="audioSrc" type="audio/mp3" />
    </audio>
    <div class="object__image-wrapper">
      <img class="object__image" src="@/assets/images/1.jpg" />
    </div>
    <div @click="activate">
      <div
        style="
          position: absolute;
          transform: translate(-40%, -50%);
          width: 232px;
          height: 165px;
          border-radius: 50%;
          cursor: pointer;
          /*background: rgba(255, 0, 0, 15%);*/
        "
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    audio: {
      type: String,
      required: true,
    },
  },

  emits: ["activate"],

  data() {
    return {
      isActivated: false,
    };
  },

  methods: {
    activate() {
      const audio = this.$refs.audio;

      audio.play();
      this.isActivated = true;
    },

    deactivate() {
      this.isActivated = false;
    },
  },

  computed: {
    audioSrc() {
      return new URL(`../../assets/sounds/${this.audio}.mp3`, import.meta.url).href;
    },
  },
};
</script>

<style lang="scss">
@keyframes object1 {
  from {
    transform: none;
  }
  5% {
    transform: rotate(6deg) translateY(-15px);
  }
  15% {
    transform: scale(1.05) rotate(-7deg) translateY(-25px);
  }
  25% {
    transform: scale(1.07) rotate(2deg) translateY(-50px);
  }
  to {
    transform: none;
  }
}

.object {
  width: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 0;
  &_activated {
    animation: object1 2.5s ease 0s 3 normal;
  }

  &__image {
    width: 300px;
    height: auto;
    pointer-events: none;
  }

  &__image-wrapper {
    width: 0;
    height: 0;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
