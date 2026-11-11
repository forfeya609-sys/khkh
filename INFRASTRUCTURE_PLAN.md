# NEURAL CUT AI — INFRASTRUCTURE & SCALING PLAN
**Version:** 1.0.0  

---

## 1. Local Development Environment
- **Frontend:** Vite Dev Server running on `http://localhost:5173` with WebSocket HMR.
- **Backend:** FastAPI running with Uvicorn on `http://localhost:8000` with automatic reload.
- **Media Engine:** Local filesystem storage mounted under `backend/storage` with proxy generation.

## 2. Production Scaled Environment
- **Frontend Serving:** Distributed Edge CDN (Cloudflare / Netlify / Vercel) serving pre-compiled static assets and WebCodecs workers.
- **API Cluster:** Dockerized FastAPI instances running behind an Nginx or Traefik reverse proxy with SSL termination.
- **Asynchronous Processing Workers:** Celery / Redis queue workers dedicated to FFmpeg render encoding and OpenCV vision analysis.
- **Object Storage:** S3-compatible object storage (AWS S3, Cloudflare R2, MinIO) with pre-signed upload/download URLs.
- **Hardware Acceleration:** GPU worker nodes with NVIDIA NVENC/NVDEC for hardware-accelerated 4K H.264/HEVC/AV1 encoding.
