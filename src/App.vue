<script setup lang="ts">
import { onMounted, onBeforeUnmount, reactive } from "vue";
import StudentClicker from "@/StudentClicker.vue";
import DataOutput from "@/DataOutput.vue";
import BuyMenu from "@/BuyMenu.vue";

const state = reactive({
  nStudents: 0,
  nTutors: 0,
  nTeachers: 0,
  nProfessors: 0,
  timerId: 0
});

const tutorSPS = 2;
const teacherSPS = 20;
const professorSPS = 100;

onMounted(() => {
  state.timerId = setInterval(() => {
    state.nStudents += (1 / 60) * tutorSPS * state.nTutors;
    state.nStudents += (1 / 60) * teacherSPS * state.nTeachers;
    state.nStudents += (1 / 60) * professorSPS * state.nProfessors;
  }, 1000 / 60);
});

onBeforeUnmount(() => {
  clearInterval(state.timerId);
});

function click () {
  state.nStudents++;
}

function buyTutor (params: { price: number }) {
  if (state.nStudents >= params.price) {
    state.nStudents -= params.price;
    state.nTutors++;
  }
}

function buyTeacher (params: { price: number }) {
  if (state.nStudents >= params.price) {
    state.nStudents -= params.price;
    state.nTeachers++;
  }
}

function buyProfessor (params: { price: number }) {
  if (state.nStudents >= params.price) {
    state.nStudents -= params.price;
    state.nProfessors++;
  }
}
</script>

<template>
  <header>
    <nav class="navbar bg-light">
      <div class="container-fluid">
        <span class="navbar-brand mb-0 h1 ms-2 fs-3">THM-Clicker</span>
      </div>
    </nav>
  </header>
  <main>
    <div class="container">
      <StudentClicker @counter = "click" />

      <DataOutput :n-students = "state.nStudents"
                  :n-tutors = "state.nTutors"
                  :n-teachers = "state.nTeachers"
                  :n-professors = "state.nProfessors"
      />

      <BuyMenu  @did-buy-tutor ="buyTutor" :n-tutors = "state.nTutors"
                @did-buy-teacher ="buyTeacher" :n-teachers = "state.nTeachers"
                @did-buy-professor ="buyProfessor" :n-professors = "state.nProfessors"
      />
    </div>
  </main>
</template>

<style scoped>

</style>
