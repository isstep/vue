<template>
  <div id="app">
    <h1>To-Do List</h1>
    <TaskInput @add-task="addTask" />
    <TaskList 
      :tasks="tasks" 
      @toggle-complete="toggleComplete" 
      @delete-task="deleteTask" 
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import TaskInput from './components/TaskInput.vue'
import TaskList from './components/TaskList.vue'

const tasks = ref([])

const addTask = (task) => {
  tasks.value.push({ id: Date.now(), text: task, completed: false })
}

const toggleComplete = (taskId) => {
  const task = tasks.value.find(t => t.id === taskId)
  if (task) {
    task.completed = !task.completed
  }
}

const deleteTask = (taskId) => {
  tasks.value = tasks.value.filter(t => t.id !== taskId)
}
</script>

<style scoped>
#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background: #f9f9f9;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}
</style>
  