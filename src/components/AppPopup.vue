<script setup lang="ts">
interface Props {
  popupContent: {
    success: boolean,
    word: string
  }
}

defineEmits(['retry']);
defineProps<Props>()
</script>

<template>
  <div class="popup-container">
    <div class="popup">
      <h2 v-if="popupContent.success">Вы победили! 😃</h2>
      <h2 v-else>Вы проиграли. 😕</h2>
      <h3>{{popupContent.word}}</h3>
      <button @click="$emit('retry')">Сыграть еще раз</button>
    </div>
  </div>
</template>

<style scoped lang="scss">

</style>