<script setup lang="ts">
interface Props {
  incorrectLetters: Array<string>
}

defineProps<Props>()
</script>

<template>
  <div class="wrong-letters-container">
    <h2>Ошибки</h2>
    <div class="wrong-letters" v-if="!incorrectLetters.length">
      <span>Ошибок пока нет</span>
    </div>
    <div v-else class="wrong-letters">
      <span v-for="(letter, index) in incorrectLetters" :key="index">{{letter}}; </span>
    </div>
  </div>
</template>

<style scoped lang="scss">

</style>