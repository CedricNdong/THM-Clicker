<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

const props = defineProps<{
  nStudents: number,
  nTutors: number,
  nTeachers: number,
  nProfessors: number
}>();

const emits = defineEmits<{
  (e: 'didBuyTutor', eventParams: { price: number }): void
  (e: 'didBuyTeacher', eventParams: { price: number }): void
  (e: 'didBuyProfessor', eventParams: { price: number }): void
}>();

function calculatePriceTutor() {
  return 10 + Math.pow(props.nTutors, 2);
}

function calculatePriceTeacher() {
  return 200 + Math.pow(props.nTeachers, 2.5);
}

function calculatePriceProfessor() {
  return 10000 + Math.pow(props.nProfessors, 3);
}

function onBuyTutor () {
  emits('didBuyTutor', { price: calculatePriceTutor() });
}

function onBuyTeacher () {
  emits('didBuyTeacher', { price: calculatePriceTeacher() });
}

function onBuyProfessor () {
  emits('didBuyProfessor', { price: calculatePriceProfessor() });
}

</script>

<template>
  <div class=" border border-secondary m-5 p-3 rounded">
    <p class="fw-semibold fs-5"> Buy </p>
    <ul class="list-group">
      <li class="list-group-item text-light">
        <button :disabled="nStudents < calculatePriceTutor()" type="button" class = "bg-primary rounded m-2 p-2  text-light" @click = "onBuyTutor">Tutor (2 S/s)
          <span class = "bg-danger rounded m-1 p-1 ms-3 text-light">  Price: {{ calculatePriceTutor() }} Students </span>
        </button>
      </li>

      <li class="list-group-item text-light">
        <button :disabled="nStudents < calculatePriceTeacher()" type="button" class = "bg-primary rounded m-2 p-2  text-light" @click = "onBuyTeacher">Teacher (20 S/s)
          <span class = "bg-danger rounded m-1 p-1 ms-3 text-light">  Price: {{ calculatePriceTeacher() }} Students </span>
        </button>
      </li>

      <li class="list-group-item text-light">
        <button :disabled="nStudents < calculatePriceProfessor()" type="button" class = "bg-primary rounded m-2 p-2  text-light" @click = "onBuyProfessor">Professor (100 S/s)
          <span class = "bg-danger rounded m-1 p-1 ms-3 text-light">  Price: {{ calculatePriceProfessor() }} Students </span>
        </button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
button:disabled {
  opacity: 0.5;
}
</style>
