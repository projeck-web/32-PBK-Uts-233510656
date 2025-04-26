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
const removeTask = (index) => {
  tasks.value.splice(index, 1)
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
      <ul class="task-list">
      <li v-for="(task, index) in filteredTasks" :key="index" class="task-item">
        <button class="cancel-btn" @click="removeTask(index)">Batalkan</button>
      </li>
    </ul>
    </div>
</template>

<style>

</style>
