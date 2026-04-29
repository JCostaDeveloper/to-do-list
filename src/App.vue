<template>
  <div class="container">
    <h1>Lista de Tarefas</h1>

    <div class="task-input">
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Digite uma nova tarefa" />
      <button @click="addTask">Adicionar</button>
    </div>

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <!-- <XMarkIcon class="w-4 h-4" @click="removeTask(index)" /> -->
         <!-- <XMarkIcon class="w-6 h-6 text-red-500 hover:text-red-700 cursor-pointer" @click="removeTask(index)" /> -->
         <img src="../public/x.png" @click="removeTask(index)" />
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { CheckIcon, TrashIcon , XMarkIcon} from '@heroicons/vue/24/solid'

const newTask = ref('');
const tasks = ref<string[]>([]);



function addTask() {
  if (newTask.value.trim()) {
    tasks.value.push(newTask.value.trim());
    newTask.value = '';
  }
}

function removeTask(index: number) {
  tasks.value.splice(index, 1);
}
</script>

<style lang="css">
.container {
  max-width: 400px;
  margin: 50px auto;
  font-family: Arial, sans-serif;
  text-align: center;
  color: white;
}
.task-input {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
input {
  flex: 1;
  padding: 8px;
}
button {
  padding: 8px 12px;
  cursor: pointer;
  background-color: #a4a5a4;
  color: white;
  border: none;
  border-radius: 4px;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #45a049;
  transform: scale(1.05);
}
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}
body {
  background-color: black;
}
</style>