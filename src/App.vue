<script setup>
import { ref } from 'vue'
// componentsフォルダ以下に作成したcomponentをimport
import AppHeader from './components/AppHeader.vue';

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

<!-- v-ifで要素がある時だけulタグを出す -->
<!-- v-showでdisplay:noneを付与する方法もある -->
<ul v-if="todos.length > 0">
  <li v-for=" (todo, i) in todos" :key="i">{{ todo }} <span @click="removeTodo(i)" style="cursor: pointer">x</span></li>
</ul>
<!-- v-else -->
 <p v-else>※ ToDoを追加してください</p>

</template>