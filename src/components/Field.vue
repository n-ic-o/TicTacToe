<script setup>
const props = defineProps({
  id: Number
})
</script>

<template>
  <div class="field" :class="{'border-right': id % 3 !== 0, 'border-left': id % 3 !== 1, 'border-bottom': id < 7, 'border-top': id > 3}">
    <p>X</p>
  </div>
</template>

<style scoped>
.field {
  display: flex;
  justify-content: center;
  align-items: center;
}

.border-right {
  border-right: 1px solid black;
}

.border-left {
  border-left: 1px solid black;
}

.border-bottom {
  border-bottom: 1px solid black;
}

.border-top {
  border-top: 1px solid black;
}
</style>
