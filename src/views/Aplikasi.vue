<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(true)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <div class="text-center py-10 my-10 bg-blue-300 rounded-lg mx-5 md:mx-10">
    <form @submit.prevent="addTodo">
      <div class="mx-10">
        <h1 class="font-medium text-blue-900 mb-5 text-lg">Inputkan Data Kegiatan</h1>
        <input class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" v-model="newTodo">
      </div>
      <div class="mx-auto">
        <button class="text-white my-5 bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Submit</button>
      </div>
    </form>
    <ul class="flex-row ">
      <div class="px-3 md:px-10">
        <li class="bg-blue-200 text-sm font-medium items-center justify-center mx-auto p-2.5 my-3 flex border border-none rounded-lg w-full" v-for="todo in filteredTodos" :key="todo.id">
          <input class="mr-2 h-5 w-4" type="checkbox" v-model="todo.done">
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
          <button class="ml-2 font-medium border border-none bg-blue-300 px-2 rounded-lg text-red-700" @click="removeTodo(todo)">X</button>
        </li>
      </div>
    </ul>
    <button class="my-5 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800" @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Tampilkan Semua' : 'Tampilkan yang belum selesai' }}
    </button>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>