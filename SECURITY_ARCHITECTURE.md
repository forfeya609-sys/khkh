# NEURAL CUT AI — SECURITY & DATA PRIVACY ARCHITECTURE
**Version:** 1.0.0  

---

## 1. Authentication & Session Security
- **JWT (JSON Web Tokens):** Cryptographically signed with HMAC-SHA256 using server-side secret keys.
- **Short-Lived Access Tokens:** 15-minute expiration with secure, HTTP-only refresh tokens.
- **Password Hashing:** Argon2id or Bcrypt with minimum 12 salt rounds.

## 2. File Upload & Binary Ingestion Hardening
- **Strict Magic Number Verification:** Reject files that merely rename `.exe` or `.sh` to `.mp4`. Validate ISO Base Media File Format (MP4/MOV `ftyp` box) and Matroska (`0x1A45DFA3`).
- **FFprobe Container Validation:** Reject corrupted files, zip bombs, or recursive container wrappers before handing off to processing.
- **Filename Sanitization:** Strip directory traversal payloads (`../`, `..\`), special characters, and assign UUID-based storage filenames.

## 3. Multi-Tenant Project Isolation
- Every database query for projects, media assets, and exports enforces `user_id = current_user.id`.
- Storage directory partitioning: files are segregated by user UUID (`storage/users/{user_id}/projects/{project_id}/...`).

## 4. Resource DoS & Rate Limiting
- Chunked uploads capped at 25MB per chunk.
- Concurrent video rendering limited to 2 active render jobs per standard user to prevent GPU/CPU starvation.
- Video analysis frame subsampling (e.g. 2–4 FPS probe sampling for scene classification rather than decoding all 60 frames per second unless detailed optical flow is explicitly requested).
