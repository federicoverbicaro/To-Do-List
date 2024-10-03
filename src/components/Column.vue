<template>
    <div class="bg-white shadow p-4 rounded w-1/3">
        <div class="flex  justify-between">
            <h2 class="text-xl font-semibold capitalize text-blue-500">{{ title }}</h2>

            <button @click="removeColumn" class="bg-red-500 rounded p-2 text-white">Elimina Colonna</button>
        </div>

        <ul class="mt-2">
            <li v-for="(task, index) in tasks" :key="index" class="bg-gray-200 p-2 my-1 rounded">
                {{ task }}
            </li>
        </ul>
        <div class="flex justify-between gap-3">
            <input v-model="newTask" type="text" placeholder="Aggiungi un'attività" class="p-2 border rounded" />
            <button @click="addTask" class="bg-blue-500 text-white p-2 rounded h-10">Aggiungi</button>
        </div>

    </div>
</template>
<script>
export default {
    props: {
        title: String,
        tasks: Array
    },

    data() {
        return {
            newTask: ''
        }
    },

    methods: {
        addTask() {
            if (this.newTask.trim()) {
                this.$emit('add-task', this.newTask)
                this.newTask = ''
            }
        },

        removeColumn() {
            this.$emit('remove-column') // Emetti l'evento 'remove-column' per il genitore
        }

    }
}
</script>
