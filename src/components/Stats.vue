<script setup>
import { ref } from 'vue'

let xwins = ref(0)
let owins = ref(0)

const addWin = (winner) => {
  if (winner === 'x') {
    xwins.value++
  } else if (winner === 'o') {
    owins.value++
  }
}
</script>

<template>
  <div class="stats">
    <p class="winstats">{{ xwins }} : {{ owins }}</p>
  </div>
</template>

<style scoped>
.stats {
  width: 100%;
  height: 100%;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
.winstats {
  font-size: 12rem;
  color: var(--color-text);
}
</style>