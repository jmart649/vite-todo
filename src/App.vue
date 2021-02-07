<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <header class="flex flex-col container">
      <h1 class="text-6xl text-center italic font-bold text-blue-700 underline">To Do APP</h1>
      <input class="text-2xl font-light italic rounded-xl py-2 px-4 mt-4" type="text" placeholder="New To Do" v-model="newTodo" @change="addTodo" />
    </header>
    <main class="container w-full mt-8">
      <section>
        <h3 class="text-2xl font-thin text-green-600">PENDING: {{ pendingTodos.length }}</h3>
        <ul class="space-y-2">
          <li v-for="todo in pendingTodos" :key="todo.id" class="bg-white rounded-xl py-2 px-4 font-bold italic text-center hover:bg-green-500 cursor-pointer" @click="changeStatus(todo.id)">{{ todo.text }}</li>
        </ul>
      </section>
      <section>
        <h3 class="text-2xl font-thin text-red-600">COMPLETED: {{ completedTodos.length }}</h3>
        <ul class="space-y-4">
          <li v-for="todo in completedTodos" :key="todo.id" class="bg-white font-bold rounded-xl py-2 px-4 italic text-center hover:bg-red-500 cursor-pointer" @click="changeStatus(todo.id)">{{ todo.text }}</li>
        </ul>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const newTodo = ref('')

const todos = ref([])

const pendingTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'pending'),
)

const completedTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'done'),
)

const changeStatus = id => {
  todos.value.map(todo => {
    if(todo.id === id) {
      todo.status = todo.status === 'pending' ? 'done' : 'pending'
    }
  })
}

const addTodo = () => {
  if (newTodo.value.length>0){
    todos.value.push({
      id:todos.value.length,
      text:newTodo.value,
      status:'pending'
    })
    newTodo.value = ''
  }
}
</script>