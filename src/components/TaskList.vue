<template>
    <ul class="task-list">
      <li v-for="task in tasks" :key="task.id" :class="{ completed: task.completed }">
        <input type="checkbox" v-model="task.completed" @change="toggleComplete(task.id)" />
        <span>{{ task.text }}</span>
        <button @click="deleteTask(task.id)">Delete</button>
      </li>
    </ul>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue'
  
  const props = defineProps({
    tasks: Array
  })
  
  const emit = defineEmits(['toggle-complete', 'delete-task'])
  
  const toggleComplete = (taskId) => {
    emit('toggle-complete', taskId)
  }
  
  const deleteTask = (taskId) => {
    emit('delete-task', taskId)
  }
  </script>
  
  <style scoped>
  .task-list {
    list-style: none;
    padding: 0;
  }
  
  .task-list li {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px;
    border-bottom: 1px solid #ddd;
  }
  
  .task-list li.completed span {
    text-decoration: line-through;
    color: #999;
  }
  
  button {
    padding: 5px 10px;
    font-size: 14px;
    background: #dc3545;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background: #c82333;
  }
  </style>
  