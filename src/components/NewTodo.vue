<template>
    <input class="text-2xl font-light italic rounded-xl py-2 px-4 mt-4" type="text" placeholder="New To Do" v-model="newTodo" @change="addTodo" />
</template>

<script setup>
import { newTodo, addTodo } from '../helpers/useTodos'
</script>