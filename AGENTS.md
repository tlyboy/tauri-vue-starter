# AGENTS.md

This file provides guidance to AI agents when working with code in this repository.

## Development Commands

```bash
# Start Tauri development mode (frontend + Rust backend)
pnpm tauri dev

# Start frontend development server only
pnpm dev

# Build for production
pnpm build

# Build Tauri application
pnpm tauri build

# Preview production build
pnpm preview
```

## Architecture Overview

This is a Tauri 2 + Vue 3 desktop application project.

### Frontend (Vue 3)

- **Routing**: File-system routing using `unplugin-vue-router`, pages are in the `src/pages/` directory
- **Layouts**: Using `vite-plugin-vue-layouts`, layout files are in the `src/layouts/` directory
- **Auto-imports**:
  - Vue/VueUse/Pinia APIs are auto-imported (no manual import needed)
  - Components under `src/components/` are auto-registered
  - Files under `src/composables/` and `src/stores/` are auto-imported
- **State Management**: Pinia + pinia-plugin-persistedstate (state persistence)
- **Styling**: Tailwind CSS 4 + @egoist/tailwindcss-icons (icons via CSS classes)

### Backend (Rust/Tauri)

- Tauri commands are defined in `src-tauri/src/lib.rs`
- Use `#[tauri::command]` macro to define functions callable from the frontend
- Frontend calls Rust commands via `@tauri-apps/api`

### Path Alias

- `@/` maps to the `src/` directory
