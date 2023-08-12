<script setup>
import Field from './Field.vue'
import { ref } from 'vue'

let currentplayer = ref('x')

const handleClick = () => {
  currentplayer.value = currentplayer.value === 'x' ? 'o' : 'x'
}

const getcurrentplayer = () => {
  return currentplayer.value
}
</script>

<template>
  <div class="gamefield">
    <Field v-for="i in 9" :key="i" :id = "i" @fieldclicked="handleClick" :currentplayer="getcurrentplayer" />
  </div>
</template>

<style scoped>
.gamefield {
  width: 100%;
  height: 100%;
  padding: 1rem;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  border-right: 4px solid var(--color-text);
  /*box-shadow: 0 0 5px 5px #48abe0;*/
}
</style>