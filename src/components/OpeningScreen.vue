<template>
  <Transition>
    <div v-if="isOpened" class="opening-screen">
      <h1 class="opening-screen__title">reversal</h1>
      <div class="opening-screen__text">
        this is a visual poem based on<br />
        a lecture of gestalt therapist<br />
        Guiseppe Iaculo
      </div>
      <button
        class="opening-screen__button"
        :class="{ 'opening-screen__button_hoverable': isButtonSeen }"
        @animationstart.once="isButtonSeen = true"
        @click="isButtonSeen ? close() : null"
      >
        please enter
      </button>
    </div>
  </Transition>
</template>

<script setup>
import { ref, onMounted } from "vue";

const emit = defineEmits(["opened"]);

const isOpened = ref(true),
  isButtonSeen = ref(false),
  close = () => {
    isOpened.value = false;
    document.body.style.overflow = "";
    emit("opened");
  };

onMounted(() => {
  document.body.style.overflow = "hidden";
});
</script>

<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes flickering {
  from {
    opacity: 0.5;
  }
  to {
    opacity: 1;
  }
}

.opening-screen {
  background: white;
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  bottom: 0;
  z-index: 1000;
  color: black;

  &__title {
    position: absolute;
    left: 50%;
    top: 30.5%;
    font-size: 92px;
    transform: translate(-50%, -50%);
    opacity: 0;
    animation: 1s ease 0.5s fade-in;
    animation-fill-mode: forwards;

    letter-spacing: 4px;
  }

  &__text {
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 23px;
    font-style: italic;
    line-height: 1.2;
    opacity: 0;
    animation: 1s ease 2s fade-in;
    animation-fill-mode: forwards;
    top: 47%;
    letter-spacing: 0.5px;
  }

  &__button {
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    background: transparent;
    border: none;
    color: black;
    animation: 1s ease 5s fade-in;
    animation-fill-mode: both;
    cursor: default;
    top: 61%;
    font-style: italic;
    font-size: 51px;

    &_hoverable {
      animation-fill-mode: none;
      cursor: pointer;
      &:hover {
        animation: 0.3s ease 0 flickering;
        animation-iteration-count: infinite;
      }
    }
  }
}
</style>
