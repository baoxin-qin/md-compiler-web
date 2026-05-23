# md-compiler-web

- Web 在线 Markdown 解析渲染器，前端部分；基于 Vue 3 + TypeScript + Vite 实现。
- 后端部分基于 Python + FastAPI 实现。[点击前往](https://github.com/baoxin-qin/md-compiler-server)

## 技术选型

| 技术 | 描述 |
| --- | --- |
| Vue 3 | 前端框架 |
| TypeScript | 前端类型 |
| Vite | 前端构建工具 |
| CodeMirror | 简易版代码编辑器 |

## 项目结构

```text
src/
|———— assets/
|     |———— markdown.css  # HTML 预览效果专用样式文件
|———— components/
|     |———— Preview.vue  # 预览组件
|     |———— Editor.vue  # 编辑器组件
|———— App.vue  # 根组件
|———— main.ts  # 入口文件
|———— style.css # 全局样式文件
```

## 快速开始

> 注：**该项目为前后端分离实现，需同时启动前端和后端项目**

- 安装依赖
```bash
npm install
```
- 运行项目
```bash
npm run dev
```