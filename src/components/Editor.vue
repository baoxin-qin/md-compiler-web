<script setup lang="ts">
import { ref } from 'vue';
import { Codemirror } from 'vue-codemirror';
import { markdown } from '@codemirror/lang-markdown';

const content = ref('');
</script>

<template>
    <div class="editor-container">
        <div class="tool-bar">
            <h1 class="title">在线 Markdown 解析渲染器</h1>
            <input class="file-input" type="file" accept=".md" />
            <button class="submit-btn">点击渲染</button>
        </div>
        <Codemirror
            class="editor"
            v-model="content"
            :extensions="[markdown()]"
            placeholder="Edit your code here ..."
        />
    </div>
</template>

<style scoped>
.editor-container {
    grid-column: 1 / 2;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.tool-bar {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-shrink: 0;
    padding: 10px 0;
}
.title {
    color: #333;
    font-size: 25px;
    text-align: center;
}
.submit-btn {
    width: 100px;
    height: 40px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f5f5f5;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.1s ease-in-out;
}
.submit-btn:active {
    background-color: #d5d5d5;
}

.editor {
    flex: 1;
    margin: 0;
    min-height: 0;
    resize: none;
    overflow: auto;
}
:deep(.cm-editor) {
    height: 100%;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
    outline: none;
}
:deep(.cm-scrollbar) {
    overflow: auto;
}
</style>