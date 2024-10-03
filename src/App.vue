<script>
import Column from './components/Column.vue';


export default {
  name: 'App',
  components: {
    Column
  },

  data() {
    return {
      columns: []
    }
  },

  mounted() {
    const storedColumns = localStorage.getItem('columns')
    if (storedColumns) {
      this.columns = JSON.parse(storedColumns)
    };


  },

  methods: {
    addTask(index, task) {
      if (task) {
        this.columns[index].tasks.push(task)
        this.saveToLocalStorage();
      }
    },
    removeColumn(index) {
      this.columns.splice(index, 1) 
      this.saveToLocalStorage()   
    },

    saveToLocalStorage() {
      localStorage.setItem('columns', JSON.stringify(this.columns))
    },

    addColumn() {
      const newColumnTitle = prompt('Inserisci il nome della nuova colonna')
      if (newColumnTitle) {
        this.columns.push({
          title: newColumnTitle, tasks: []
        })
        this.saveToLocalStorage();
      }
    }
  },
}

</script>

<template>
  <div class="bg-gray-100 min-h-screen p-4 overflow-y-scroll ">
    <div class="text-center mb-10">
      <h1 class="text-4xl text-green-500 uppercase">To Do List Parsonale</h1>
    </div>
    <button @click="addColumn" class="mt-4 bg-green-500 text-white p-2 rounded">Aggiungi Colonna</button>

    <div class="flex  gap-5 mt-4">
      <Column v-for="(column, index) in columns" :key="index" :title="column.title" :tasks="column.tasks"
        @add-task="addTask(index, $event)" @remove-column="removeColumn(index)" />
    </div>

  </div>


</template>
