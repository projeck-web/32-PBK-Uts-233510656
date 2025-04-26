<script setup>
import { ref, computed } from 'vue'

const newTask = ref('')
const showOnlyIncomplete = ref(false)
const tasks = ref([
  { text: 'berkebun', done: false },
  { text: 'belajar javascript', done: false },
  { text: 'mengerjakan tugas', done: false }
])

</script>

<template>
  <div class="paragraf">
    <h1>Laras 233510656</h1>
  </div>

  <div class="app-container">
    <h1 class="title">Daftar Kegiatan</h1>
  </div>
</template>

<style>

</style>
