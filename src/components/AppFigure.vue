<script setup lang="ts">
interface Props {
  incorrectLetters: Array<string>
}

defineProps<Props>()
</script>

<template>
  <svg v-if="incorrectLetters.length !== 0" height="250" width="200" class="figure-container"
       preserveAspectRatio="xMidYMid meet">

    <!-- Rod -->
    <g v-if="incorrectLetters.length >=1">
      <line x1="60" y1="20" x2="140" y2="20"/>
      <line x1="140" y1="20" x2="140" y2="50"/>
      <line x1="60" y1="20" x2="60" y2="230"/>
      <line x1="20" y1="230" x2="100" y2="230"/>
    </g>


    <!-- Head -->
    <circle v-if="incorrectLetters.length >=2" cx="140" cy="70" r="20"/>

    <!-- Body -->

    <line v-if="incorrectLetters.length >=3" x1="140" y1="90" x2="140" y2="150"/>
    <!-- Arms -->

    <line v-if="incorrectLetters.length >=4" x1="140" y1="120" x2="120" y2="100"/>
    <line v-if="incorrectLetters.length >=5" x1="140" y1="120" x2="160" y2="100"/>


    <!-- Legs -->

    <line v-if="incorrectLetters.length >=6" x1="140" y1="150" x2="120" y2="180"/>
    <line v-if="incorrectLetters.length >=7" x1="140" y1="150" x2="160" y2="180"/>

  </svg>

  <svg v-else width="100%" height="100%" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid meet">
    <!-- Face -->
    <circle cx="50" cy="50" r="40" fill="yellow" stroke="black" stroke-width="2"/>

    <!-- Left Eye -->
    <circle cx="35" cy="40" r="5" fill="black"/>

    <!-- Right Eye -->
    <circle cx="65" cy="40" r="5" fill="black"/>

    <!-- Mouth -->
    <path d="M30 60 Q50 80 70 60" fill="transparent" stroke="black"/>
  </svg>

</template>

<style scoped lang="scss">

</style>