<script setup>
import { ref } from 'vue'

const props = defineProps({
  xwins: {
    type: Number,
    required: true
  },
  owins: {
    type: Number,
    required: true
  }
})

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