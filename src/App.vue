<script setup>
import { ref } from 'vue'
const number = ref(0)

const add = () => {
  number.value++
}
</script>
<template>
<input type="text" size="30" v-model="number">
<!-- v-on:click を @click に省略できる -->
<button @click="add()">+1</button>
</template>