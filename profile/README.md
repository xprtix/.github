<div align="center">

  <img src="https://xprtix.com/favicon.svg" alt="XPRTIX Logo" width="80" height="80" />

  # XPRTIX

  **In-Browser Media Utilities & SVG Editor for Creative Engineering**

  *Every file, export-ready. 100% private, client-side, WebAssembly-powered.*

  [![Website](https://img.shields.io/badge/Website-xprtix.com-151515?style=for-the-badge&logo=googlechrome&logoColor=white)](https://xprtix.com)
  [![License](https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge)](#-license)
  [![Privacy](https://img.shields.io/badge/Privacy-100%25%20Local-success?style=for-the-badge)](https://xprtix.com/privacy)
  [![X (Twitter)](https://img.shields.io/badge/X-%40xprtix-black?style=for-the-badge&logo=x)](https://x.com/xprtix)

</div>

---

## ⚡ Overview

**XPRTIX** is a zero-framework, privacy-first web utility suite built for developers, designers, and privacy-conscious creators. It eliminates heavy desktop vector software and slow server-based video converters by running low-latency media processing directly in your browser.

No file uploads for local tasks. No accounts. No watermarks. No file size limits for client-side processing.

---

## 🛠️ Included Tool Modules

### 🎨 1. In-Browser SVG Vector Editor (`xprtix.com/svg`)
A full-screen, multi-artboard vector workstation running entirely in vanilla JavaScript and the DOM.
* **Path & Node Editing:** Pen tool, node/anchor point reshaping, control points, and multi-path manipulation.
* **Shape & Boolean Operations:** Powered by Paper.js for boolean union, subtract, intersection, stroke outlining, and path simplification.
* **Full Workstation Features:** Multi-artboard document tabs, full undo/redo stack, and custom gradient styling.
* **Export Engine:** Export clean, optimized **SVG**, high-DPI **PNG**, **JPG**, **WebP**, or native **React component (JSX/TSX)** code.

### 🎬 2. iOS Video Playback Repair (`xprtix.com/video`)
Diagnoses and repairs MP4/MOV videos that fail to play inline on iPhone, iPad, and Safari.
* **Faststart Repair:** Custom-written client-side MP4 parser/rewriter relocates the `moov` atom header to the front of the file bit-for-bit without re-encoding.
* **HEVC Tagging Fix:** Rewrites `hev1` container tags to `hvc1` in-browser for native Apple Media Source Extensions compatibility.
* **Fallback Stream Re-Encoding:** Server fallback (capped at 50 MB) using FFmpeg re-encodes unsupported video codecs to H.264 and non-conforming audio to AAC.

### 🖼️ 3. Image Processing & Format Engine (`xprtix.com/image`)
Offloads image transformations to dedicated Web Workers to ensure a 60 FPS UI during heavy operations.
* **Format Conversion:** Convert between **HEIC** (via `libheif` WebAssembly), **AVIF** (via custom WASM encoder), **WebP**, **PNG**, **JPEG**, **PDF**, and multi-size **ICO** favicons.
* **Batch Operations:** Crop, scale, compress (via `fflate`), and package batch downloads into ZIP archives locally.
* **Privacy Controls:** Strips EXIF metadata and GPS location information automatically prior to saving.

---

## 🎯 Programmatic Quick Links (`Popular Tasks`)

Jump directly to dedicated intent-matched conversion routes:

| Utility | Task | Direct Route |
| :--- | :--- | :--- |
| 🖼️ Image | **HEIC → JPG** | [`xprtix.com/image/heic-to-jpg`](https://xprtix.com/image/heic-to-jpg) |
| 🎨 SVG | **SVG → PNG** | [`xprtix.com/svg/svg-to-png`](https://xprtix.com/svg/svg-to-png) |
| 🎬 Video | **MOV → MP4** | [`xprtix.com/video/mov-to-mp4`](https://xprtix.com/video/mov-to-mp4) |
| 🖼️ Image | **PNG → WebP** | [`xprtix.com/image/png-to-webp`](https://xprtix.com/image/png-to-webp) |
| 🖼️ Image | **Compress PNG** | [`xprtix.com/image/compress-png`](https://xprtix.com/image/compress-png) |
| 🎨 SVG | **SVG → React Component** | [`xprtix.com/svg/svg-to-react`](https://xprtix.com/svg/svg-to-react) |
| 🖼️ Image | **PNG → Favicon (ICO)** | [`xprtix.com/image/png-to-ico`](https://xprtix.com/image/png-to-ico) |
| 🎬 Video | **Fix iPhone No-Sound Video** | [`xprtix.com/video/no-sound-on-iphone`](https://xprtix.com/video/no-sound-on-iphone) |

---

## 🔒 Security & Local Privacy Architecture

1. **Local-First Executables:** Custom MP4 container rewriter, image converter Web Workers, and the SVG editor run completely client-side in your browser.
2. **Transparent Fallback:** Files are uploaded to the Node backend only when a video requires a full FFmpeg stream re-encode (e.g., unsupported codecs/audio). Uploads are purged immediately after processing.
3. **Anonymous Telemetry:** Minimal, non-identifying operational analytics from the Video and Image tools are sent to `api.xprtix.com` to monitor performance without user tracking.

---

## ⚙️ Architecture & Tech Stack

### Frontend (Browser)
* **Core:** Vanilla HTML5, CSS3, and JavaScript (ES Modules) — zero UI frameworks.
* **Routing:** Single HTML document with a hand-written SPA router for instant route switches (`/`, `/video`, `/image`, `/svg`).
* **Design System:** Geist & Geist Mono (Google Fonts), tokenized CSS variables matching brand design specs.
* **Vendored Libraries (`web/vendor/`):**
  * `paper.js` — SVG path boolean operations, smoothing, and stroke outlining.
  * `libheif` (WASM) — Client-side HEIC decoding.
  * `AVIF encoder` (WASM) — Client-side AVIF encoding.
  * `fflate` — Fast ZIP archive construction and PNG compression.

### Backend (Server)
* **Runtime:** Node.js 18+ with Express 4 (only 2 external dependencies).
* **Media Server:** `multer` for multipart video uploads; `ffmpeg` + `ffprobe` for server-side H.264/AAC re-encoding.
* **Dynamic SSR:** Generates route-specific HTML, programmatic landing pages, sitemap, and custom 404 views.

### Build, Test & CI/CD
* **Bundler:** `esbuild` for minification and content-hashed production builds (`dist/`).
* **Test Runner:** Native `node:test` test runner.
* **Infrastructure:** Linux VPS running Nginx as a reverse proxy, SSL via Certbot (Let's Encrypt), and PM2 process management.
* **Deployment:** Automated GitHub Actions workflow executing SSH deployment and PM2 reloads on pushes to `main`.

---

## 👤 Author & Maintainer

Built with precision by **Moamen Sherif**:

* **Website:** [moamen-sherif.com](https://moamen-sherif.com)
* **GitHub:** [@MoamenSherif81](https://github.com/MoamenSherif81)
* **X (Twitter):** [@MoamenSherif81](https://x.com/MoamenSherif81)
* **LinkedIn:** [Moamen Sherif](https://www.linkedin.com/in/moamen-sherif)

---

## 📄 License

Copyright © 2026 XPRTIX / Moamen Sherif. All Rights Reserved.

XPRTIX is a proprietary software platform. Unauthorized copying, modification, or redistribution of this repository's codebase is strictly prohibited.

---

<div align="center">

  **XPRTIX** (`/ˈɛks.pər.tɪks/`) — *Export and expert, in one word.*

</div>
