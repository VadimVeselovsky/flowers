<template>
  <Transition>
    <div v-if="isOpened" class="opening-screen">
      <button class="opening-screen__button" @click="close">Открыть</button>
    </div>
  </Transition>
</template>

<script setup>
import { ref, onMounted } from "vue";

const emit = defineEmits(["opened"]);

const isOpened = ref(true),
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

.opening-screen {
  background: white;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1000;

  &__button {
    border: none;
    background: #4a4a4a;
    color: white;
    padding: 11px;
    border-radius: 5px;
    position: absolute;
    top: 50vh;
    left: 50vw;
    transform: translateX(-50%);
    cursor: pointer;
  }
}
</style>
