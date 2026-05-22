<script setup lang="ts">
import { ref } from 'vue';
import Editor from './components/Editor.vue';
import Preview from './components/Preview.vue';

const result = ref('');
</script>

<template>
	<div class="container">
		<Editor :result="result" @update="(val) => result = val"/>
		<Preview :result="result"/>
	</div>
</template>

<style scoped>
.container{
	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 20px;
	margin: auto;
	height: 100%;
	padding: 0 20px;
}
</style>