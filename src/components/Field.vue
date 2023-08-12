<script setup>
import { ref } from 'vue'

const props = defineProps({
  id: Number,
  currentplayer: Function
})

const emit = defineEmits(['fieldclicked'])

let fieldvalue = ref('')

const setField = () => {
  if (fieldvalue.value === '') {
    fieldvalue.value = props.currentplayer()
    console.log(props.currentplayer())
    emit('fieldclicked')
  }
}
</script>

<template>
  <div class="field" :class="{'border-right': id % 3 !== 0, 'border-bottom': id < 7}" @click="setField">
    <i class="fa-solid fa-circle xl" v-if="fieldvalue === 'o'"></i>
    <i class="fa-solid fa-times xxl" v-if="fieldvalue === 'x'"></i>
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
</style>
