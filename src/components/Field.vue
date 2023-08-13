<script setup>
import { ref } from 'vue'

const props = defineProps({
  id: Number,
  currentplayer: Function,
  gamefield: Array,
  gameover: Array
})

const emit = defineEmits(['fieldclicked'])

let mousehover = ref(false)
</script>

<template>
  <div class="field" :class="{'border-right': id % 3 !== 0, 'border-bottom': id < 7}" @click="emit('fieldclicked', id)" @mouseover="mousehover = true" @mouseleave="mousehover = false">
    <i class="fa-solid fa-circle xl" v-if="gamefield.find((f) => f.id === id && f.player === 'o')" :class="{'win': props.gameover.includes(id)}"></i>
    <i class="fa-solid fa-times xxl" v-if="gamefield.find((f) => f.id === id && f.player === 'x')" :class="{'win': props.gameover.includes(id)}"></i>

    <i class="fa-solid fa-circle xl grey" v-if="props.currentplayer() === 'o' && mousehover && !gamefield.find((f) => f.id === id) && !props.gameover.length"></i>
    <i class="fa-solid fa-times xxl grey" v-if="props.currentplayer() === 'x' && mousehover && !gamefield.find((f) => f.id === id) && !props.gameover.length"></i>
  </div>
</template>

<style scoped>
.field {
  display: flex;
  justify-content: center;
  align-items: center;
}

.border-right {
  border-right: 1px solid var(--color-text);
}

.border-bottom {
  border-bottom: 1px solid var(--color-text);
}

.xl {
  font-size: 7rem;
}

.xxl {
  font-size: 10rem;
}

.grey {
  color: rgb(44, 44, 44);
}

.win {
  color: gold;
}
</style>
