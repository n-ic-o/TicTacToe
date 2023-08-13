<script setup>
import Field from './Field.vue'
import { ref } from 'vue'

let currentplayer = ref('x')
let gamefield = ref([])
let gameover = ref([])

const handleClick = (field) => {
  if (gameover.value.length > 0) {
    return
  }
  if (gamefield.value.find((f) => f.id === field)) {
    return
  }
  gamefield.value.push({ id: field, player: currentplayer.value })
  if (calculateWinner(currentplayer.value)) {
    addWin(currentplayer.value)
    return
  }
  currentplayer.value = currentplayer.value === 'x' ? 'o' : 'x'
}

const calculateWinner = (player) => {
  for (let i = 0; i < 3; i++) {
    if (gamefield.value.filter((f) => f.id % 3 === i && f.player === player).length === 3) {
      for (let j = 0; j < 3; j++) {
        gameover.value.push(i + j * 3)
      }
      return true
    }
  }
  if (gamefield.value.filter((f) => f.id < 4 && f.player === player).length === 3) {
    for (let i = 1; i < 4; i++) {
      gameover.value.push(i)
    }
    return true
  }
  if (gamefield.value.filter((f) => f.id > 3 && f.id < 7 && f.player === player).length === 3) {
    for (let i = 4; i < 7; i++) {
      gameover.value.push(i)
    }
    return true
  }
  if (gamefield.value.filter((f) => f.id > 6 && f.id < 10 && f.player === player).length === 3) {
    for (let i = 7; i < 10; i++) {
      gameover.value.push(i)
    }
    return true
    }
  if (gamefield.value.filter((f) => (f.id === 1 && f.player === player) || (f.id === 5 && f.player === player) || (f.id === 9 && f.player === player)).length === 3) {
    for (let i = 1; i < 10; i += 4) {
      gameover.value.push(i)
    }
    return true
  }
  if (gamefield.value.filter((f) => (f.id === 3 && f.player === player) || (f.id === 5 && f.player === player) || (f.id === 7 && f.player === player)).length === 3) {
    for (let i = 3; i < 8; i += 2) {
      gameover.value.push(i)
    }
    return true
  }
  return false
}

const addWin = (winner) => {
  setTimeout(() => {
    newGame()
  }, 2000)
}

const getcurrentplayer = () => {
  return currentplayer.value
}

const newGame = () => {
  gamefield.value = []
  currentplayer.value = 'x'
  gameover.value = []
}
</script>

<template>
  <div class="gamefield">
    <Field v-for="i in 9" :key="i" :id = "i" @fieldclicked="handleClick" :currentplayer="getcurrentplayer" :gamefield="gamefield" :gameover="gameover" />
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