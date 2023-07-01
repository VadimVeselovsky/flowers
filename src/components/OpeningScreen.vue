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
        @mouseup="isButtonSeen ? close() : null"
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
  close = () =>
    setTimeout(() => {
      isOpened.value = false;
      document.body.style.overflow = "";
      emit("opened");
    }, 1300);

onMounted(() => {
  document.body.style.overflow = "hidden";
});
</script>

<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
  transition: opacity 2s ease;
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
  from,
  49% {
    background-image: url(@/assets/images/opening/1.jpg);
  }
  50%,
  to {
    background-image: url(@/assets/images/opening/2.jpg);
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
  user-select: none;

  &__title {
    position: absolute;
    left: 50%;
    top: 30.5%;
    font-size: 92px;
    transform: translate(-50%, -50%);
    opacity: 0;
    animation: 1.5s ease 1s fade-in;
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
    animation: 1.5s ease 3.4s fade-in;
    animation-fill-mode: forwards;
    top: 47%;
    letter-spacing: 0.5px;
    z-index: 5;
  }

  &__button {
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);
    background: transparent;
    border: none;
    color: black;
    animation: 1s ease 8s fade-in;
    animation-fill-mode: both;
    cursor: default;
    top: 63%;
    font-style: italic;
    font-size: 36px;
    background-position: center;
    background-repeat: no-repeat;
    border-radius: 50%;
    background-position: 30% 1%;
    background-position: center;
    background-size: 100% 100%;
    height: 200px;
    width: 285px;
    background-image: url(@/assets/images/opening/2.jpg);
    outline: none !important;
    border: none !important;
    transition: 0.2s background-image;
    &:hover {
      background-image: url(@/assets/images/opening/1.jpg);
    }
    &:active {
      opacity: 0.5 !important;
    }

    &_hoverable {
      cursor: pointer;
    }
  }
}
</style>
