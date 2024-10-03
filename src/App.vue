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

  mounted(){
    const storedColumns = localcStorage.getItem('columns')
    if(storedColumns){
      this.columns = JSON.parse(storedColumns)
    }
  },

  methods:{
    addTask(index, task){
      if(task){
        this.columns[index].task.push(task)
        this.saveToLocalStorage;
      }
    },
    addColumn(){
      const newColumnTitle = prompt ('INserisci il nome della nuova colonna')
      if(newColumnTitle){
        this.columns.push({
        title:newColumnTitle, tasks: []
        })
      }
    }


  },

  saveToLocalStorage(){
    localcStorage.setItem('columns', JSON.stringify(this.columns))
  }

}

</script>

<template>
  <div class="bg-gray-100 min-h-screen p-4">
    <div class="text-center mb-10">
      <h1 class="text-3xl">To Do List Parsonale</h1>
    </div>

    <div class="flex justify-between mt-4">
      <Column v-for="(column, index) in columns" :key="index" :title="column.title" :tasks="column.tasks" @add-task="addTask(index, $event)"/>
    </div>
    <button @click="addColumn" class="mt-4 bg-green-500 text-white p-2 rounded">Aggiungi Colonna</button>
  </div>


</template>
