<script setup lang="ts">
interface PreviewProps {
    result: string;
}
const props = defineProps<PreviewProps>();
</script>

<template>
    <div class="preview-container">
        <h1 class="title">预览结果</h1>
        <div class="preview-content" v-html="props.result"></div>
    </div>
</template>

<style scoped>
.preview-container {
    grid-column: 2 / 3;
    border-left: 1px solid #ccc;
    height: 100%;
    padding: 0 10px;
    overflow: auto;
}
.title {
    font-size: 18px;
    padding-bottom: 10px;
    border-bottom: 1px dashed #ccc;
}
</style>

<style src="src/assets/markdown.css"></style>