# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 开发命令

```bash
# 启动 Tauri 开发模式（前端 + Rust 后端）
pnpm tauri dev

# 仅启动前端开发服务器
pnpm dev

# 构建生产版本
pnpm build

# 构建 Tauri 应用
pnpm tauri build

# 预览生产构建
pnpm preview
```

## 架构概览

这是一个 Tauri 2 + Vue 3 桌面应用项目。

### 前端 (Vue 3)

- **路由**: 使用 `unplugin-vue-router` 实现文件系统路由，页面放在 `src/pages/` 目录
- **布局**: 使用 `vite-plugin-vue-layouts`，布局文件放在 `src/layouts/` 目录
- **自动导入**:
  - Vue/VueUse/Pinia API 自动导入（无需手动 import）
  - `src/components/` 下的组件自动注册
  - `src/composables/` 和 `src/stores/` 下的文件自动导入
- **状态管理**: Pinia + pinia-plugin-persistedstate（状态持久化）
- **样式**: Tailwind CSS 4 + @egoist/tailwindcss-icons（图标通过 CSS class 使用）

### 后端 (Rust/Tauri)

- Tauri 命令定义在 `src-tauri/src/lib.rs`
- 使用 `#[tauri::command]` 宏定义可从前端调用的函数
- 前端通过 `@tauri-apps/api` 调用 Rust 命令

### 路径别名

- `@/` 映射到 `src/` 目录
