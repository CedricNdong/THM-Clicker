<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
  nStudents: number,
  nTutors: number,
  nTeachers: number,
  nProfessors: number
}>();

const formatNumber = (number: number) => {
  if (number >= 1_000_000) {
    return (number / 1_000_000).toFixed(1) + ' M';
  }
  if (number >= 1_000) {
    return (number / 1_000).toFixed(1) + ' k';
  }
  return Math.floor(number);
};
</script>

<template>
  <div class="border border-secondary m-5 p-3 rounded">
    <p class="fw-semibold fs-5"> Inventory </p>
    <ul class="list-group">
      <Transition name="slide">
        <li class="list-group-item" v-if="props.nStudents > 0 ">Students:
          <span class="bg-primary text-light rounded m-2 p-1">{{ formatNumber(props.nStudents) }}</span>
        </li>
      </Transition>

      <Transition name="slide">
        <li class="list-group-item" v-if="props.nTutors > 0 ">Tutors:
          <span class="bg-primary text-light rounded m-2 p-1">{{ formatNumber(props.nTutors) }}</span>
        </li>
      </Transition>

      <Transition name="slide">
        <li class="list-group-item" v-if="props.nTeachers > 0 ">Teachers:
          <span class="bg-primary text-light rounded m-2 p-1">{{ formatNumber(props.nTeachers) }}</span>
        </li>
      </Transition>

      <Transition name="slide">
        <li class="list-group-item" v-if="props.nProfessors > 0 ">Professors:
          <span class="bg-primary text-light rounded m-2 p-1">{{ formatNumber(props.nProfessors) }}</span>
        </li>
      </Transition>


    </ul>
  </div>
</template>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: all 1s ease;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-50px);
}
</style>
