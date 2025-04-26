<script setup>
import { ref, computed } from 'vue'

const newTask = ref('')
const showOnlyIncomplete = ref(false)
const tasks = ref([
  { text: 'berkebun', done: false },
  { text: 'belajar javascript', done: false },
  { text: 'mengerjakan tugas', done: false }
])
const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push({ text: newTask.value, done: false })
    newTask.value = ''
  }
}

</script>

<template>
  <div class="paragraf">
    <h1>Laras 233510656</h1>
  </div>

  <div class="app-container">
    <h1 class="title">Daftar Kegiatan</h1>
  </div>
  <div class="form">
      <input v-model="newTask" placeholder="Tambahkan kegiatan..." @keyup.enter="addTask" />
      <button @click="addTask">Tambah</button>
    </div>
</template>

<style>

</style>
