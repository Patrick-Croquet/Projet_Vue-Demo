<script setup>
import TodoItem from './components/TodoItem.vue'
</script>

<template>
    <div>
      <h2>Liste de tâches</h2>
      <ul>
        <TodoItem
          v-for="(todo, index) in todos"
          :key="index"
          :task-text="todo.text"
          :is-done.sync="todo.done"
          @toggle-done="toggleTodo(index)"
        />
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        todos: [
          { text: 'Apprendre Vue.js', done: false },
          { text: 'Faire les courses', done: false },
          { text: 'Terminer ce projet', done: false },
          { text: 'Réaliser un nouveau projet', done: true },
        ]
      }
    },
    methods: {
      toggleTodo(index) {
        this.todos[index].done = !this.todos[index].done;
      }
    }
  }
  </script>
  