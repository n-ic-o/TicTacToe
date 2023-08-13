<script setup>
import GameField from './GameField.vue'
import Stats from './Stats.vue'
import { ref } from 'vue'

</script>

<template>
  <div class="container">
    <div class="box">
      <GameField />
    </div>
    <div class="box">
      <Stats />
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