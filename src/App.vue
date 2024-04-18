<script setup lang="ts">
import words from "@/store/names";
import TheHeader from "@/components/TheHeader.vue";
import AppFigure from "@/components/AppFigure.vue";
import AppWrongLetters from "@/components/AppWrongLetters.vue";
import AppWord from "@/components/AppWord.vue";
import {computed, onMounted, ref} from "vue";
import AppNotification from "@/components/AppNotification.vue";
import AppPopup from "@/components/AppPopup.vue";

// interface PopupInfo {
//   success: boolean;
//   word: string;
// }
function getRandomName(): string {
  const randomIndex = Math.floor(Math.random() * words.length);
  return words[randomIndex];
}

const notificationFlag = ref(false);

const word = ref(getRandomName());
console.log(word.value);

const letters = ref<Array<string>>([]);
const correctLetters = computed(() => letters.value.filter(letter => word.value.includes(letter)))
const incorrectLetters = computed(() => letters.value.filter(letter => !word.value.includes(letter)))
const handleKeydown = ({key}: KeyboardEvent): void => {
  if (/[а-яё]/.test(key) && !notificationFlag.value) {
    if (letters.value.includes(key)) {
      showNotification()
    } else {
      letters.value.push(key)
    }
  }
}

const showPopup = computed(() => {
  if (incorrectLetters.value.length === 7) {
     window.removeEventListener('keydown', handleKeydown)
    return {
      success: false,
      word: word.value
    }
  } else if (correctLetters.value.length === new Set(word.value).size) {
     window.removeEventListener('keydown', handleKeydown)
    return {
      success: true,
      word: word.value
    }
  }
})

const handleRetry = (): void => {
  letters.value = [];
  word.value = getRandomName();
  console.log(word.value);

  window.addEventListener('keydown', handleKeydown)
};

const showNotification = (): void => {
  notificationFlag.value = true;
  setTimeout(() => {
    notificationFlag.value = false
  }, 1000)
}
window.addEventListener('keydown', handleKeydown)
</script>

<template>
  <the-header/>

  <div class="game-container">
    <app-word :word="word" :correct-letters="correctLetters"/>
    <app-figure :incorrect-letters="incorrectLetters"/>
    <app-wrong-letters :incorrect-letters="incorrectLetters"/>
  </div>

  <app-notification v-if="notificationFlag"/>
  <app-popup v-if="showPopup" :popup-content="showPopup" @retry="handleRetry"/>
</template>

<style lang="scss">

</style>
