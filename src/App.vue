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

const filteredTasks = computed(() => {
  return showOnlyIncomplete.value
    ? tasks.value.filter(task => !task.done)
    : tasks.value
})
</script>

<template>
  <div class="paragraf">
    <h1>Laras 233510656</h1>
  </div>
  <div class="app-container">
    <h1 class="title">Daftar Kegiatan</h1>

    <div class="form">
      <input v-model="newTask" placeholder="Tambahkan kegiatan..." @keyup.enter="addTask" />
      <button @click="addTask">Tambah</button>
    </div>

    <div class="filter">
      <label>
        <input type="checkbox" v-model="showOnlyIncomplete" /> Kegiatan yang belum selesai
      </label>
    </div>

    <ul class="task-list">
      <li v-for="(task, index) in filteredTasks" :key="index" class="task-item">
        <input type="checkbox" v-model="task.done" />
        <span :class="{ done: task.done }">{{ task.text }}</span>
        <button class="cancel-btn" @click="removeTask(index)">Batalkan</button>
      </li>
    </ul>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(to right, #000000, #78daf5);
}

.paragraf {
  margin-bottom: 5px;
  font-size: 1.4rem;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
body {
  display: flex;
  justify-content: center;
  align-items: center;
}

.app-container {
  width: 74vw;
  height: 75vh;
  padding: 40px 20px;
  background: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow-y: auto;
  border-radius: 15px;
}

.title {
  margin-bottom: 15px;
  color: #333;
}

.form {
  display: flex;
  gap: 10px;
  width: 100%;
  max-width: 600px;
  margin-bottom: 20px;
}

.form input {
  flex: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 14px;
  font-size: 1rem;
  background: #a9a8a8;
  color: #000000;

}

.form button {
  padding: 10px 15px;
  background: #4caf50;
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 1rem;
}

.filter {
  margin-bottom: 20px;
  font-size: 14px;
  color: #666;
}

.task-list {
  list-style: none;
  padding: 0;
  width: 100%;
  max-width: 600px;
  
}

.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #b3b1b1;
  padding: 10px;
  border-radius: 10px;
  margin-bottom: 15px;
  border: 2px solid #515050;
}

.task-item span {
  flex: 1;
  margin-left: 10px;
  font-size: 1rem;
  color: black;
}

.task-item span.done {
  text-decoration: line-through;
  color: #686666;
}

.cancel-btn {
  background: #f44336;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 0.9rem;
}
</style>