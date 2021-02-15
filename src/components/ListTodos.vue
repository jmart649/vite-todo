<template>
    <section>
    <h3 class="text-2xl underline font-bold" :class="color === 'green' ? 'text-green-800' :'text-red-800'"> {{ title }}: {{ todos.length }}</h3>
    <ul class="space-y-2">
        <li v-for="todo in todos" :key="todo.id" class="bg-white rounded-xl py-2 px-4 font-bold italic text-center hover:text-blue-800 cursor-pointer" @click="changeStatus(todo.id)">{{ todo.text }}</li>
    </ul>
    </section>
</template>

<script setup>
import { defineProps } from 'vue'
import { pendingTodos, changeStatus } from '../helpers/useTodos'

defineProps({
    color: {
        type: String,
        default: 'green',
    },
    title: {
        type: String,
        default: 'Todo List',
    },
    todos: {
        type: Array,
        default: [],
    },
})
</script>