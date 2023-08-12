<script setup>
import Field from './Field.vue'
</script>

<template>
  <div class="gamefield">
    <Field v-for="i in 9" :key="i" :id = "i"/>
  </div>
</template>

<style scoped>
.gamefield {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}
</style>