<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:152671,50:5669bd,100:afbeff&height=200&section=header&text=VIVI%20Music%20Canvas&fontSize=64&fontColor=ffffff&fontAlignY=38&desc=Custom%20Background%20Visuals%20for%20vivi-music&descAlignY=58&descSize=18&animation=fadeIn" width="100%"/>

<br/>

[![Status](https://img.shields.io/badge/Status-Live-brightgreen?style=for-the-badge&logoColor=white&labelColor=152671&color=22c55e)](#)
[![Validation](https://img.shields.io/badge/CI-Automated-blue?style=for-the-badge&logo=githubactions&logoColor=white&labelColor=152671&color=5669bd)](#)
[![License](https://img.shields.io/badge/License-GPL_3.0-blue?style=for-the-badge&logo=opensource&logoColor=white&labelColor=152671&color=5669bd)](LICENSE)

<br/>
<br/>

<img src="App%20Logo/vivimusic.png" alt="ViviMusic Logo" width="140" height="140" style="border-radius: 24px; box-shadow: 0 10px 30px rgba(0,0,0,0.5);">

<br/>
<br/>

> **The central mapping and repository block for serving gorgeous, looping background videos (Canvases) natively inside the [`vivi-music`](https://github.com/vivizzz007/vivi-music) Android application.**

<br/>

</div>

---

## ✦ What is VIVI Music Canvas?

This repository acts as the central hub for hosting and mapping custom `.m3u8` or `.mp4` background videos to specific songs or albums within VIVI Music. 

Any modifications pushed to this repository are automatically validated by our CI/CD pipeline and deployed directly to the VIVI Music Canvas Content Delivery Network (CDN) at `vivimusicanvas.mkmdevilmi.workers.dev`.

---

## 🚀 How to Add a Canvas

If you find a stunning visualizer or music video clip that perfectly fits a song, you can add it to the app globally by following these steps:

### 1. Upload Your Video
Drop your looping video file natively inside the `Song/` or `Album/` directories within this repository.
*Example: `Song/blinding_lights_loop.m3u8`*

### 2. Map It in `canvas.json`
Open the `canvas.json` file located in the root of the repository. Add a new block to the `"items"` array precisely mapping the exact song name, artist, and album to your new video URL.

```jsonc
{
  "items": [
    {
      "song": "Blinding Lights",
      "artist": "The Weeknd",
      "album": "After Hours",
      // Important: Ensure the URL points to our deployed domain!
      "url": "https://vivimusicanvas.mkmdevilmi.workers.dev/Song/blinding_lights_loop.m3u8"
    }
  ]
}
```

### 3. Open a Pull Request

When opening a Pull Request (PR), **you must include the original song/album link** (YouTube Music, Spotify, or similar) in the description. This enables maintainers to verify the metadata formatting and ensure perfect audio-visual syncing.

> **Pull Request Example:**
> - **Title:** `feat: added canvas for Blinding Lights by The Weeknd`
> - **Description:** Added `Song/20.m3u8` for Blinding Lights.
> - **Original Link:** `https://music.youtube.com/watch?v=4NRXx6U8ABQ`

---

## 🤖 Automated Validation Check

To ensure pristine playback performance and zero broken links in the app, this repository features an automated **Validation Bot** that strict-checks every Pull Request:

| Check | Description |
|---|---|
| **JSON Syntax** | Ensures `canvas.json` is beautifully formatted and lacks trailing commas. |
| **Schema Match** | Verifies `song`, `artist`, `album`, and `url` keys explicitly exist. |
| **File Integrity** | Verifies the video referenced in the URL physically exists in the repository. |
| **Deduplication** | Scans and rejects duplicate `(song, artist, album)` combinations. |

*You can run this validation suite locally prior to pushing using Node.js:*
```bash
node scripts/validate_canvas.js
```

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:afbeff,50:5669bd,100:152671&height=100&section=footer" width="100%"/>

<sub>**Vivi Music Project © 2026** · All rights reserved · Built for [`vivi-music`](https://github.com/vivizzz007/vivi-music)</sub>

</div>
