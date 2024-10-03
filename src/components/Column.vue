<template>
    <div class="bg-white shadow p-4 rounded w-1/3 h-screen">
        <div class="flex  justify-between mb-8">
            <h2 class="text-3xl font-semibold capitalize text-blue-500">{{ title }}</h2>

            <button @click="removeColumn" class="bg-red-500 rounded p-2 text-white">Elimina Colonna</button>
        </div>
        <div class="mt-8 gap-3">
            <button @click="addTask"  class="bg-blue-500 text-white p-2 rounded h-10 mb-3 w-full">Aggiungi</button>
            <input v-model="newTask" @keydown.enter="addTask" type="text" placeholder="Aggiungi un'attività" class="p-2 border rounded w-full" />
        </div>

        <div class="flex items-end flex-col h-auto mt-3">
            <ul v-for="(task, index) in tasks" :key="index" class=" w-full flex gap-3 ">
                <li>
                    <button @click="removeTask(index)"
                        class="bg-red-500 rounded p-2 my-1 text-white h-10">Elimina</button>
                </li>

                <li class="bg-gray-200 p-2 my-1 w-full rounded text-blacl capitalize">
                    {{ task }}
                </li>
            </ul>
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
            this.$emit('remove-column')
        },

        removeTask(index) {
            this.$emit('remove-task', index)
        },
    }
}
</script>
