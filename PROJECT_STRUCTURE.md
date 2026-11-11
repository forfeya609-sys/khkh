# NEURAL CUT AI — PROJECT STRUCTURE & DIRECTORY MAP
**Project Name:** NEURAL CUT AI  
**Architecture:** Full-Stack Video Production Suite  

```
c:\Users\Admin\Downloads\KOL\
├── backend/                              # Python FastAPI Video Processing Backend
│   ├── app/
│   │   ├── api/                          # REST & WebSocket Endpoints
│   │   │   ├── auth.py                   # User registration, login, JWT
│   │   │   ├── projects.py               # Project CRUD & versioning
│   │   │   ├── upload.py                 # Chunked upload, validation, ffprobe
│   │   │   ├── analysis.py               # Real CV, audio & scene analysis
│   │   │   ├── research.py               # Game Knowledge & mechanics search
│   │   │   ├── director.py               # AI Director blueprint generation
│   │   │   ├── render.py                 # FFmpeg timeline composition & rendering
│   │   │   └── ws.py                     # WebSocket real-time progress broadcast
│   │   ├── core/                         # Configuration, Security, DB session
│   │   │   ├── config.py
│   │   │   ├── security.py
│   │   │   └── database.py
│   │   ├── models/                       # SQLAlchemy / Pydantic Data Models
│   │   ├── services/                     # Core Business & Processing Logic
│   │   │   ├── video_analyzer.py         # OpenCV / SceneDetect & beat tracking
│   │   │   ├── game_researcher.py        # Game knowledge base & mechanics
│   │   │   ├── director_engine.py        # AMV / Cinematic editing planner
│   │   │   └── ffmpeg_renderer.py        # FFmpeg filter-complex builder
│   │   └── main.py                       # FastAPI application entry point
│   ├── storage/                          # Managed Local Media Tiers
│   │   ├── originals/                    # Raw uploaded videos
│   │   ├── proxies/                      # 720p fast editing proxies
│   │   ├── thumbnails/                   # Extracted keyframe thumbnails
│   │   ├── previews/                     # Lightweight web preview clips
│   │   ├── rendered/                     # Rendered master files
│   │   └── exports/                      # Platform-optimized final exports
│   └── requirements.txt
│
├── public/                               # Static Frontend Assets
│   └── vite.svg
│
├── src/                                  # React 19 Frontend Workspace
│   ├── assets/                           # Branding, icons, logos
│   ├── components/                       # 15 Core Studio Views & Modules
│   │   ├── dashboard/                    # 01. Dashboard
│   │   ├── project/                      # 02. New Project Creator
│   │   ├── upload/                       # 03. Upload Center (Chunked & Resumable)
│   │   ├── analysis/                     # 04. AI Analysis Center
│   │   ├── research/                     # 05. Game Research Center
│   │   ├── director/                     # 06. AI Director Studio
│   │   ├── editor/                       # 07. Main Editing Studio
│   │   ├── motion/                       # 08. Motion Graphics Studio
│   │   ├── sound/                        # 09. Sound Design Studio
│   │   ├── subtitle/                     # 10. Subtitle Studio
│   │   ├── library/                      # 11. Asset Library
│   │   ├── render/                       # 12. Render Center
│   │   ├── export/                       # 13. Export Center
│   │   ├── history/                      # 14. Project History & Versions
│   │   ├── settings/                     # 15. User & System Settings
│   │   ├── header/                       # Top Navigation & Quick Switcher
│   │   ├── monitor/                      # Live Real-time Compositor Monitor
│   │   ├── timeline/                     # Professional Multi-Track NLE Timeline
│   │   ├── inspector/                    # Properties & Keyframes Panel
│   │   ├── interview/                    # Creative Onboarding Wizard
│   │   └── qc/                           # Quality Control & Compliance Check
│   ├── data/                             # Stock Assets & Game Databases
│   ├── engine/                           # Client-side Realtime Compositing Engines
│   │   ├── videoCompositor.ts            # HTML5 Canvas 2D + Effects Compositor
│   │   ├── audioEngine.ts                # Web Audio API Sound Generator & Synthesizer
│   │   ├── autoEditingEngine.ts          # Client-side Director Logic
│   │   ├── exportEngine.ts               # Client-side MediaRecorder Exporter
│   │   └── qcEngine.ts                   # Broadcast QC Rules
│   ├── stores/                           # Zustand Global Reactive Stores
│   │   ├── useEditorStore.ts             # Master Timeline & Project State
│   │   ├── useAssetStore.ts              # Media Library Store
│   │   ├── useInterviewStore.ts          # Creative Interview Store
│   │   ├── useGameResearchStore.ts       # Game Intelligence Store
│   │   └── useNavigationStore.ts         # Studio Center Router Store
│   ├── types/                            # TypeScript Type Definitions
│   ├── App.tsx                           # Master Shell & Studio Router
│   ├── App.css                           # Layout Styles
│   ├── index.css                         # Tailwind CSS Directives & Custom Fonts
│   └── main.tsx                          # Frontend Entry
│
├── dist/                                 # Production Frontend Distribution
├── package.json                          # Frontend Dependencies & Scripts
├── tsconfig.json                         # TypeScript Project Config
└── vite.config.ts                        # Vite Configuration & Backend Proxy
```
