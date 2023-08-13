<script setup>
import GameField from './GameField.vue'
import Stats from './Stats.vue'
import { ref } from 'vue'

let xwins = ref(0)
let owins = ref(0)

const handleWin = (winner) => {
  if (winner === 'x') {
    xwins.value++
  } else if (winner === 'o') {
    owins.value++
  }
}

</script>

<template>
  <div class="container">
    <div class="box">
      <GameField @win="handleWin" />
    </div>
    <div class="box">
      <Stats :xwins="xwins" :owins="owins" />
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
}

.box {
  width: 50%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>