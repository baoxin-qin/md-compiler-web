<script setup lang="ts">
import Editor from './components/Editor.vue';
import Preview from './components/Preview.vue';
</script>

<template>
	<div class="container">
		<Editor />
		<Preview />
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