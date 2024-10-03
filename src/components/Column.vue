<template>
    <div class="bg-white shadow p-4 rounded w-1/3">
        <h2 class="text-xl font-semibold text-center">{{ title }}</h2>
        <ul class="mt-2">
            <li v-for="(task,index) in tasks" :key="index" class="bg-gray-200 p-2 my-1 rounded">
                {{ task }}
            </li>
        </ul>
        <input v-model="newTask" type="text" placeholder="Aggiungi un'attività" class="p-2 border rounded my-2"/>
        <button @click="addTask" class="bg-blue-500 text-white p-2 rounded">Aggiungi</button>
    </div>
</template>
<script>
export default {
    props:{
        title: String,
        tasks: Array
    },

    data(){
        return{
            newTask: ''
        }
    },

    methods: {
        addTask(){
            if (this.newTask.trim()){
                this.$emit('add-task',this.newTask)
                this.newTask = ''
            }
        }
    }
}
</script>
