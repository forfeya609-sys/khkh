# NEURAL CUT AI — SYSTEM ARCHITECTURE SPECIFICATION
**Version:** 1.0.0  
**Phase:** PHASE 01 — System Architecture  

---

## 1. System Overview

NEURAL CUT AI is an automated AI Video Production Studio designed to transform raw gameplay, anime clips, and media recordings into polished, professional-grade video montages (AMVs, Gaming Montages, and Social Media Reels) through an intelligent end-to-end pipeline:

```
[ USER MEDIA ]
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 1. UPLOAD & INGESTION PIPELINE                         │
│    - Chunked streaming, MIME validation, FFprobe       │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 2. AI VIDEO ANALYSIS ENGINE                            │
│    - Optical flow motion, scene cuts, audio spectral   │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 3. GAME RESEARCH ENGINE (Knowledge Graph)              │
│    - HUD, character skill detection, combat mechanics  │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 4. AI CREATIVE DIRECTOR                                │
│    - Story blueprint, pacing curve, beat sync plan     │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 5. PROFESSIONAL NLE EDITING ENGINE                     │
│    - 4-Track compositing, velocity ramps, color grade  │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 6. MOTION, SOUND & SUBTITLE GRAPHICS ENGINE            │
│    - Combo counters, impact SFX, kinetic typography    │
└────────────────────────────────────────────────────────┘
      │
      ▼
┌────────────────────────────────────────────────────────┐
│ 7. RENDER & MULTI-PLATFORM EXPORT                      │
│    - WebCodecs/Canvas Compositor & FFmpeg Master       │
└────────────────────────────────────────────────────────┘
```

---

## 2. Frontend Layer (React 19 + TypeScript + Tailwind v4 + Zustand)

- **Application Shell (`App.tsx`):** Hosts the global header, master studio navigation, and routes between the 15 specialized centers.
- **Master State Hub (`useEditorStore.ts`):** Single source of truth for:
  - Active Project metadata & version history.
  - Multi-track timeline state (Tracks, Clips, Playhead, Snap, Zoom).
  - Selected clip inspector properties (Effects, Color Grading, Speed Ramps, Subtitles).
- **Navigation State Hub (`useNavigationStore.ts`):** Manages active studio tab with state persistence.
- **Real-Time Video Compositor (`VideoCompositor.ts`):**
  - High-performance Canvas 2D render loop operating at 60 FPS.
  - Custom pixel shader transformations (RGB split, bloom, flash, shake, glitch, vignettes).
- **Audio Synthesizer & Web Audio Graph (`AudioEngine.ts`):**
  - Multi-bus audio mixing (BGM track, SFX track, Speech track).
  - Procedural sound generation for instantaneous UI feedback without network lag.

---

## 3. Backend Layer (Python FastAPI + OpenCV + FFmpeg Pipeline)

- **RESTful API Gateway:** Handles authentication, project CRUD, file uploads, analysis triggers, and export jobs.
- **WebSocket Gateway (`/ws`):** Provides live progress updates for long-running AI video analysis and video rendering tasks.
- **Computer Vision Service:**
  - Fast scene cut detection via frame color histograms and luminance variance.
  - Motion intensity estimation via Farneback dense optical flow.
  - Combat event detection (explosions, flashes, rapid position shifts).
- **Audio Processing Service:**
  - Beat and tempo (BPM) detection using spectral onset strength.
  - Energy peak detection for synching impacts to drum kicks.
- **Rendering Service:**
  - FFmpeg filter-complex generator for lossless 4K export with hardware acceleration (NVENC / QuickSync when available).

---

## 4. Multi-Platform Delivery & Storage Model

```
storage/
├── originals/   # Immutable raw user uploads (MP4, MOV, MKV, WebM)
├── proxies/     # Fast 720p 30fps H.264 proxy files for zero-latency timeline scrubbing
├── thumbnails/  # WebP keyframe preview thumbnails
├── previews/    # Rendered 1080p preview streams
├── rendered/    # Full master rendered video files
└── exports/     # Platform-optimized exports (TikTok 9:16, YouTube 16:9, Insta 1:1)
```
