<script setup>
// 親から子コンポーネントに値を送るのがprops
defineProps(['todos'])

// 子から親に渡すのがemit
const emit = defineEmits('removeTodo')

// clickした時にこれがまず呼び出されて、removeTodoを呼び出す
const clickRemove = (i) => emit('removeTodo', i)

</script>

<template>
<!-- v-ifで要素がある時だけulタグを出す -->
<!-- v-showでdisplay:noneを付与する方法もある -->
<ul v-if="todos.length > 0">
  <li v-for=" (todo, i) in todos" :key="i">{{ todo }} <span @click="clickRemove(i)" style="cursor: pointer">x</span></li>
</ul>
<!-- v-else -->
 <p v-else>※ ToDoを追加してください</p>
</template>