<template>
    <div class="task-input">
      <input v-model="newTask" @keyup.enter="submitTask" placeholder="Enter a new task" />
      <button @click="submitTask">Add Task</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const newTask = ref('')
  
  const submitTask = () => {
    if (newTask.value.trim()) {
      emit('add-task', newTask.value)
      newTask.value = ''
    }
  }
  
  const emit = defineEmits(['add-task'])
  </script>
  
  <style scoped>
  .task-input {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
  }
  
  input {
    padding: 10px;
    font-size: 16px;
    border: 2px solid #ddd;
    border-radius: 4px;
    width: 70%;
    margin-right: 10px;
    box-sizing: border-box;
  }
  
  button {
    padding: 10px 20px;
    font-size: 16px;
    background: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background: #218838;
  }
  </style>
  