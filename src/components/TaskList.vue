<template>
    <div>
      <ul>
        <li v-for="(todo, index) in todos" :key="index" class="bg-white shadow p-2 my-2 rounded border border-gray-400">
          {{ todo }}
        </li>
      </ul>
      <div class="flex gap-4 items-end">
        <input v-model="newTodo" type="text" placeholder="Aggiungi una nuova attività" class="p-2 border rounded w-80" />
        <button @click="addTodo" class="bg-blue-500 text-white px-2 h-10 rounded ">Aggiungi</button>
      </div>
     
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        todos: [],
        newTodo: ''
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo !== '') {
          this.todos.push(this.newTodo);
          this.newTodo = '';
        }
      }
    }
  }
  </script>
  
  <style scoped>
  /* Stili specifici per il componente TodoList */
  </style>
  