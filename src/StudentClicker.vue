<script setup lang="ts">
import { defineEmits } from 'vue';

const emit = defineEmits<{
  (e: 'counter', eventParams: { value: number }): void
}>();
function click () {
  emit('counter', { value: 0 });
}

</script>

<template>
  <div class=" border border-secondary m-5 p-3 rounded">
    <button type="button" class="fs-1 rounded border border-info btn btn-outline-info" @click = "click">👨‍🎓</button>
  </div>
</template>

<style scoped>
.fs-1:hover {
  transform: scale(1.15);
  transition: transform 0.2s;
}

.fs-1:active {
  transform: scale(0.9);
  transition: transform 0.2s;
}

</style>