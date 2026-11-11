# NEURAL CUT AI — KNOWN ISSUES & TECHNICAL DEBT REGISTER
**Date:** November 11, 2026  

---

## 1. Discovered Issues & Technical Constraints

### ISSUE-01: Simulated Computer Vision & Scene Detection (High Priority)
- **Problem:** `aiAnalysisEngine.ts` currently calculates scene duration and luminance scores using trigonometric math (`Math.sin(sceneIndex)`) instead of real video frame decoding.
- **Root Cause:** Initial frontend prototype was built without a server backend or client-side video decoding pipeline.
- **Resolution Plan:** Implement client-side frame extraction via hidden `<video>` element and offscreen `<canvas>` with pixel luminance/motion delta calculation, coupled with backend OpenCV/PySceneDetect pipeline for deep analysis.

### ISSUE-02: Missing Multi-Page / Studio Navigation (High Priority)
- **Problem:** User prompt Section 08 specifies 15 core centers (Dashboard, New Project, Upload Center, AI Analysis Center, Game Research Center, AI Director, Editing Studio, Motion Graphics Studio, Sound Design Studio, Subtitle Studio, Asset Library, Render Center, Export Center, Project History, Settings). Currently the application only toggles between `LandingPage` and `EditingStudio` with modal dialogs.
- **Root Cause:** Early prototype focused strictly on the timeline canvas.
- **Resolution Plan:** Implement a unified studio switcher in the application shell with dedicated views for all 15 studios while maintaining seamless live synchronization with the master timeline store.

### ISSUE-03: Branding Consistency (Medium Priority)
- **Problem:** Header and title tags display "NEXUS AI STUDIO" instead of the official project name "NEURAL CUT AI".
- **Resolution Plan:** Update application title, metadata, logos, and UI headers to NEURAL CUT AI.

### ISSUE-04: Lack of Persistent Project Database (Medium Priority)
- **Problem:** Reloading the browser currently reinitializes the demo project. Projects cannot be saved, renamed, duplicated, or restored.
- **Resolution Plan:** Implement persistent project storage in `localStorage` / IndexedDB on the frontend and SQLite/PostgreSQL backend models with full CRUD operations.

### ISSUE-05: Absence of Game Intelligence & Roblox/Gakuran Database (Medium Priority)
- **Problem:** No database or research engine exists for games, mechanics, combat terms, or special abilities.
- **Resolution Plan:** Build the Game Research Center and a dedicated knowledge base for fighting games, Roblox (e.g. Gakuran combat mechanics, combos, counters), anime, and FPS.
