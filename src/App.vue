<script setup>
import { ref } from 'vue'
// componentsフォルダ以下に作成したcomponentをimport
import AppHeader from './components/AppHeader.vue';
import TodoList from './components/TodoList.vue';

const todos = ref([])
const newTodo = ref('')

const addTodo = () => {
  todos.value.push(newTodo.value)
  newTodo.value = ''
}

const removeTodo = (index) => {
  todos.value.splice(index, 1)
}
</script>

<template>

<!-- script内に定義したcomponentを独自タグとして呼び出す -->
<AppHeader color="red">My ToDo</AppHeader>

<input type="text" size="30" v-model="newTodo">
<button @click="addTodo()">+1追加する</button>

<!-- 子から渡されたremoveTodoってどれ？を@で定義する必要がある -->
<TodoList :todos="todos" @removeTodo="removeTodo" />
</template>