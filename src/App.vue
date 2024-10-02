<script>
import TaskList from './components/TaskList.vue';


export default {
  name: 'App',
  components: {
    TaskList
  }
}

</script>

<template>
  <div class="bg-gray-100 min-h-screen p-4">
    <div class="text-center mb-10">
      <h1 class="text-3xl">To Do List Parsonale</h1>
    </div>
    <div class="bg-white w-96 p-4 rounded h-auto">
      <h1 class="text-xl font-bold text-blue-500">Lista delle cose da fare</h1>
      <div>
        <TaskList />
      </div>
    </div>
  </div>


</template>
