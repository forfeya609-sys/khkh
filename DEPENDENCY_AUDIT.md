# NEURAL CUT AI — DEPENDENCY AUDIT
**Date:** November 11, 2026  

---

## 1. Frontend Dependencies (`package.json`)

| Package | Version | Purpose | Security & Health Status |
|---|---|---|---|
| `react` | `^19.3.1` | Core UI View Library | Stable, production verified |
| `react-dom` | `^19.3.1` | DOM Renderer for React | Stable, production verified |
| `zustand` | `^5.1.0` | Global State Management | Lightweight, high performance |
| `lucide-react` | `^1.71.0` | Studio Icons | Tree-shakeable, clean SVG |
| `tailwindcss` | `^4.3.5` | Modern Utility CSS | Latest v4 engine |
| `@tailwindcss/vite` | `^4.3.5` | Vite plugin for Tailwind v4 | High-speed compilation |
| `canvas-confetti` | `^1.9.4` | Milestone / Export Celebration | Harmless, isolated |
| `vite` | `^8.3.6` | Frontend Build Tool & Dev Server | Ultra-fast HMR |
| `typescript` | `~7.0.2` | Type Safety | Strict typing passed |
| `oxlint` | `^1.90.0` | High-speed linter | Configured |

---

## 2. Host System Runtime Capabilities

| Runtime / Tool | Detected Version | Availability | Notes |
|---|---|---|---|
| **Node.js** | `v26.13.0` | Installed (`C:\Program Files\nodejs\node.exe`) | Ready for Vite frontend dev server |
| **npm** | `11.20.0` | Installed (`C:\Program Files\nodejs\npm.ps1`) | Package manager ready |
| **Python** | `3.14.7` | Installed (`C:\Users\Admin\AppData\Local\Python\pythoncore-3.14-64\python.exe`) | Ready for FastAPI backend services |
| **FFmpeg** | Not in system PATH | Standalone binary recommended | Can use bundled binary or python wrapper / fallback to browser WebCodecs/Canvas compositor |
| **Git** | Not in system PATH | Optional for local development | File versioning handled in database |

---

## 3. Required Backend Dependencies (`requirements.txt`)

For the Python FastAPI processing backend:
- `fastapi>=0.115.0`
- `uvicorn[standard]>=0.32.0`
- `pydantic>=2.9.0`
- `python-multipart>=0.0.12`
- `aiofiles>=24.1.0`
- `numpy>=2.0.0`
- `opencv-python-headless>=4.10.0` (for frame extraction & optical flow motion detection)
- `sqlite3` (built-in standard library for local project DB)
