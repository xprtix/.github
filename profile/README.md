<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/xprtix-logo-white.svg">
  <img src="assets/xprtix-logo-ink.svg" alt="XPRTIX" width="320">
</picture>

**Every file, export-ready.**

Free video, image and SVG tools that run in your browser. Your files never leave your device.

[![xprtix.com](https://img.shields.io/badge/xprtix.com-151515?style=flat-square)](https://xprtix.com)
[![Free, no account](https://img.shields.io/badge/free-no%20account-A04747?style=flat-square)](https://xprtix.com/about)
[![Privacy](https://img.shields.io/badge/files-never%20uploaded-151515?style=flat-square)](https://xprtix.com/privacy)
[![@xprtix](https://img.shields.io/badge/%40xprtix-151515?style=flat-square&logo=x)](https://x.com/xprtix)

</div>

---

## What it is

XPRTIX is a set of focused tools for developers, UI designers and creators. Each one takes a file in and hands back one that works. Everything runs in the browser: no upload, no account, no watermark.

| Tool | Route | What it does |
| :--- | :--- | :--- |
| **XPRTIX Video** | [`/video`](https://xprtix.com/video) | Fix iPhone playback, compress, convert, trim, crop, extract audio, make GIFs |
| **XPRTIX Image** | [`/image`](https://xprtix.com/image) | Convert, resize, crop and compress images, including HEIC |
| **XPRTIX SVG** | [`/svg`](https://xprtix.com/svg) | Full-screen SVG editor with node editing and React export |

## XPRTIX Video

- **iPhone fixes without re-encoding.** Moves the `moov` atom to the front (faststart) and rewrites the `hev1` tag to `hvc1`, copying the video bit for bit.
- **Compress to a size.** 16 MB for WhatsApp, 25 MB for email, 10 MB for Discord, or any size you type. You can aim for a quality instead, cap the height or frame rate, and save presets.
- **Convert.** MP4, MOV, M4V, MKV, WebM and AVI in; MP4, MOV, MKV or WebM out.
- **Edit.** Trim, crop, rotate, flip and mute. These steps re-encode at high quality.
- **Audio and GIF.** Save the sound as MP3, M4A or WAV, or up to 30 seconds as a looping GIF.
- **Size.** Videos up to about 2 GB, limited by the browser's memory.

## XPRTIX Image

- **Convert** HEIC, JPEG, PNG, WebP, AVIF, GIF and BMP to JPG, PNG, WebP, AVIF, PDF or ICO.
- **Resize, crop, rotate and compress** one image or a whole folder, and save them all as one zip.
- **Location data removed.** Saved copies leave out metadata such as camera details and GPS location.

## XPRTIX SVG

- **Draw and reshape.** Pen, shapes, node editing, gradients and boolean operations, with undo for all of it.
- **Organise.** Layers, several artboards per file, and one tab per document.
- **Export.** Optimised SVG, PNG, JPG, WebP, a React (JSX) component or a CSS data URI, with a live preview and the file size before you save.

## Popular tasks

| Task | Route |
| :--- | :--- |
| Fix hev1 video for iPhone | [`/video/hev1-to-hvc1`](https://xprtix.com/video/hev1-to-hvc1) |
| Add faststart to an MP4 | [`/video/mp4-faststart`](https://xprtix.com/video/mp4-faststart) |
| Compress a video for WhatsApp | [`/video/compress-video-for-whatsapp`](https://xprtix.com/video/compress-video-for-whatsapp) |
| Turn a video into a GIF | [`/video/video-to-gif`](https://xprtix.com/video/video-to-gif) |
| Convert MOV to MP4 | [`/video/mov-to-mp4`](https://xprtix.com/video/mov-to-mp4) |
| Convert HEIC to JPG | [`/image/heic-to-jpg`](https://xprtix.com/image/heic-to-jpg) |
| Convert PNG to WebP | [`/image/png-to-webp`](https://xprtix.com/image/png-to-webp) |
| Make a favicon from a PNG | [`/image/png-to-ico`](https://xprtix.com/image/png-to-ico) |
| Convert SVG to PNG | [`/svg/svg-to-png`](https://xprtix.com/svg/svg-to-png) |
| Convert SVG to a React component | [`/svg/svg-to-react`](https://xprtix.com/svg/svg-to-react) |

## Privacy

- **Files stay on the device.** Every tool processes files in the browser. Nothing is uploaded.
- **Extra formats load once.** For formats the browser can't read itself (for example AC-3 audio, ProRes, AVI), a small FFmpeg build (about 3 MB) is downloaded the first time and runs locally.
- **Anonymous usage data.** All three tools send anonymous usage records to `api.xprtix.com`: a random session id, the browser's user agent, the referring page, file names, sizes and formats, and what was done and whether it worked. The SVG editor sends only counts and choices. File contents are never sent. No cookies. Details: [xprtix.com/privacy](https://xprtix.com/privacy).

## How it's built

**Browser**
- Plain HTML, CSS and JavaScript modules. No UI framework.
- Video: the browser's own codecs through [Mediabunny](https://mediabunny.dev/), plus a trimmed FFmpeg WebAssembly build only for formats the browser can't read.
- Images: [libheif](https://github.com/strukturag/libheif) (WebAssembly) for HEIC, and [fflate](https://github.com/101arrowz/fflate) for zip files.
- Type: Geist and Geist Mono, with design tokens from the XPRTIX brand guidelines.

**Server**
- Node.js 18+ and Express 4. Renders each route's HTML, the landing pages, the sitemap and the 404 page.

**Build and deploy**
- `esbuild` for minified, content-hashed bundles in `dist/`.
- Tests with the built-in `node:test` runner.
- Linux VPS: Nginx reverse proxy, Let's Encrypt via Certbot, PM2.
- GitHub Actions deploys on every push to `main`, reloads PM2 and pings IndexNow.

## Third-party software

XPRTIX ships these components under their own licences:

| Component | Licence | Used for |
| :--- | :--- | :--- |
| FFmpeg (with x264 and LAME) | GPL / LGPL | Converting formats the browser can't read |
| Mediabunny | MPL-2.0 | Reading and writing video in the browser |
| libheif | LGPL-3.0 | Decoding HEIC images |
| fflate | MIT | Zip archives |

The FFmpeg build scripts and the exact configuration are published at [LINK TO PUBLIC FFMPEG BUILD REPO], as the GPL requires.

## Author

Designed, built and maintained by **Moamen Sherif**.
[moamen-sherif.com](https://moamen-sherif.com) · [GitHub](https://github.com/MoamenSherif81) · [X](https://x.com/MoamenSherif81) · [LinkedIn](https://www.linkedin.com/in/moamen-sherif)

## Licence

Copyright © 2026 Moamen Sherif. All rights reserved, except for the third-party components listed above, which keep their own licences.

---

<div align="center">

**XPRTIX** · /ˈɛks.pər.tɪks/ · Export and expert, in one word.

</div>
