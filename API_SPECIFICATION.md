# NEURAL CUT AI — API SPECIFICATION (REST & WEBSOCKET)
**Version:** 1.0.0  
**Base URL:** `/api/v1`  

---

## 1. Authentication Endpoints

- `POST /api/v1/auth/register` — Create a new user account.
- `POST /api/v1/auth/login` — Authenticate and receive JWT bearer token.
- `GET /api/v1/auth/me` — Retrieve current user profile and default preferences.
- `PUT /api/v1/auth/preferences` — Update default AI director editing preferences.

---

## 2. Projects Endpoints

- `GET /api/v1/projects` — List user's active projects with thumbnail, duration, and status.
- `POST /api/v1/projects` — Create a new project (Automatic, AMV, Gaming, Cinematic, etc.).
- `GET /api/v1/projects/{id}` — Get project metadata, timeline tracks, and clips.
- `PUT /api/v1/projects/{id}` — Update project metadata, duration, or aspect ratio.
- `POST /api/v1/projects/{id}/duplicate` — Clone project and timeline structure.
- `DELETE /api/v1/projects/{id}` — Soft delete / archive project.
- `POST /api/v1/projects/{id}/restore` — Restore archived project.

---

## 3. Upload & Media Management Endpoints

- `POST /api/v1/media/upload/init` — Initialize a chunked upload session.
- `POST /api/v1/media/upload/chunk` — Upload a binary file chunk with byte-range validation.
- `POST /api/v1/media/upload/complete` — Finalize chunk assembly, run FFprobe analysis, generate thumbnail.
- `GET /api/v1/media/assets/{id}` — Get asset details, stream URL, and proxy URL.

---

## 4. AI Video Analysis & Computer Vision Endpoints

- `POST /api/v1/analysis/scan` — Initiate frame-level scene cut, optical motion, and audio analysis.
- `GET /api/v1/analysis/reports/{asset_id}` — Retrieve detailed scene timestamps, action scores, and highlight candidates.
- `POST /api/v1/analysis/highlights/select` — Accept, modify, or reject AI candidate highlights.

---

## 5. Game Research Intelligence Endpoints

- `GET /api/v1/research/search?query={game_name}` — Query verified mechanics, characters, and combo databases.
- `POST /api/v1/research/analyze-hud` — Send a gameplay frame to identify game HUD elements, health bars, and skill icons.
- `GET /api/v1/research/gakuran` — Fetch specialized Roblox Gakuran fighting game movesets and counter timings.

---

## 6. AI Creative Director Endpoints

- `POST /api/v1/director/blueprint` — Generate complete multi-track editing blueprint (Hook, Build-up, Climax, Outro).
- `POST /api/v1/director/apply-to-timeline` — Populate timeline tracks with cuts, transitions, effects, and typography.

---

## 7. Render & Export Endpoints

- `POST /api/v1/render/start` — Queue a server-side FFmpeg rendering job (1080p, 4K, 60fps).
- `GET /api/v1/render/jobs/{job_id}` — Check render job status and download URL.
- `GET /api/v1/render/jobs/{job_id}/download` — Stream exported video file.

---

## 8. Real-Time WebSocket Channel

- `WS /api/v1/ws/project/{project_id}`
  - Receives live progress updates for:
    - Chunk upload processing
    - Frame-by-frame analysis progress (0–100%)
    - Real-time render progress and estimated time remaining (ETA)
