<script setup lang="ts">
import html2pdf from 'html2pdf.js';
import { ref } from 'vue';

interface PreviewProps {
    result: string;
}
interface Html2PdfOptions {
    margin?: number;
    filename?: string;
    image?: {
        type: 'jpeg' | 'png' | 'webp';
        quality: number;
    };
    html2canvas?: {
        scale?: number;
        useCORS?: boolean;
        logging?: boolean;
        letterRendering?: boolean;
    };
    jsPDF?: {
        unit: 'mm' | 'cm' | 'in' | 'pt';
        format: 'a4' | 'a3' | 'letter' | [number, number];
        orientation: 'portrait' | 'landscape';
    };
}

const props = defineProps<PreviewProps>();
const isDownloading = ref(false);

const handleDownload = async () => {
    if (isDownloading.value) {
        return;
    }
    
    if (!props.result || props.result.trim() === '') {
        alert("预览内容为空");
        return;
    }
    
    isDownloading.value = true;

    try {
        const previewContent = document.querySelector('.preview-content');
        if (!previewContent) {
            alert("预览内容为空");
            return;
        }
        const options: Html2PdfOptions = {
            margin: 10,
            filename: 'markdown.pdf',
            image: {type: 'jpeg', quality: 0.98},
            html2canvas: {
                scale: 2,
                useCORS: true,
            },
            jsPDF: {
                unit: 'mm',
                format: 'a4',
                orientation: 'portrait',
            }
        };
        await html2pdf().set(options).from(previewContent as HTMLElement).save();
        alert("PDF 导出成功");
    } catch (error) {
        alert("PDF 导出失败: " + error);
    } finally {
        isDownloading.value = false;
    }
}
</script>

<template>
    <div class="preview-container">
        <div class="top-bar">
            <h1 class="title">预览结果</h1>
            <button class="download-btn" @click="handleDownload" :disabled="isDownloading">
                {{ isDownloading ? '导出中...' : '导出为 PDF' }}
            </button>
        </div>
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
.top-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px dashed #ccc;
}
.title {
    font-size: 18px;
    padding-bottom: 10px;
}
.download-btn {
    width: 100px;
    height: 40px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f5f5f5;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.1s ease-in-out;
}
.download-btn:hover {
    background-color: #d5d5d5;
}
</style>

<style src="src/assets/markdown.css"></style>