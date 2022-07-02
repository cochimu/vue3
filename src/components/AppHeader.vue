<script setup>
// props親から子コンポーネントに値を送れる
defineProps(['color'])
</script>

<template>
<header>
  <h1 :style="{'color': color}">
	<!-- slot内にはデフォルト値を指定できる -->
	<slot>No Title</slot>
	</h1>
</header>
</template>