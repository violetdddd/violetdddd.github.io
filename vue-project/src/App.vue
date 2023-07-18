<template>
  <body class="bg-gray-300 h-full min-h-screen">
    <div class="container max-w-lg mx-auto py-8 px-10" >
      <h1 class="text-3xl text-center font-bold py-6">Todo List</h1>
      <form @submit.prevent="appendtodo" class="relative">
        <input type="text" v-model="mirror" class="block w-full p-4 rounded-lg border border-gray-400 text-xl text-gray-900 bg-gray-50 mb-10">
        <button type="submit" class="absolute right-2.5 bottom-2.5 px-4 py-2 rounded-lg font-semibold text-xl text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300">Add</button>
      </form>
      <div v-if="len">
        <h3 v-for="todo in todos" :key='todo'>
          <TodoItem :msg="todo" @delete="deleteTodo(todo)"></TodoItem>
        </h3>
      </div>
      <div v-else class="pt-5 text-2xl text-center">
        No todos here...
      </div>
    </div>
  </body>
</template>

<script setup lang="ts">
import TodoItem from './components/TodoItem.vue'
import {computed,ref} from 'vue'

const mirror=ref('')
const todos=ref([] as string[])
const len=computed(() => todos.value.length)

function appendtodo() {
  if (!mirror.value || todos.value.includes(mirror.value))
  return
  
  todos.value.push(mirror.value)
  mirror.value=''
}
function deleteTodo(todo: string) {
  todos.value=todos.value.filter(t => t !== todo)
}
</script>