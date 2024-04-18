<script setup lang="ts">
interface Props {
  word: string
  correctLetters: Array<string>
}

defineProps<Props>()
</script>

<template>

  <h2 class="ddd">Загаданное слово</h2>
  <div class="word">

    <span class="letter"
          v-for="(letter, index) in word"
          :key="index"
    >
      {{ correctLetters.includes(letter) ? letter : '' }}
    </span>
  </div>


</template>

<style scoped>

</style>