<!-- =========================================================================
     VIDEOPEEK PUBLIC WEBSITE
     Design by Tara Design Studio
========================================================================= -->


## 🎥 The Hero Section
![VideoPeek](https://raw.githubusercontent.com/barshasantak/videopeek/main/VideoPeek_256.png)
<br>
  
See Beneath the Frame. The native, studio-grade video specification analyzer and side-by-side A-B diff comparator engineered exclusively for macOS.
  

    ┌──────────────────────────────────────────────────────────────────────────────────────────────────────┐
    │ 📂 Open Video... │ ⚖️ Compare... │ 💾 Export JSON │ 📋 Copy │ [Report Font: A- 100% A+ ↺] 🔍 Filter  │
    ├──────────────────────────────────────────────────────────────────────────────────────────────────────┤
    │ MASTER_PRORES.mov (File A) │ [ ↔ 3 Mismatches ] │ WEB_STREAM.mp4 (File B)                            │
    │ Format: Apple ProRes 422 HQ (4K) │ Frame Drift: +2 frames │ Format: HEVC / H.265 (1080p)             │
    ├───────────────────────────────────────┴─────────────────────────┴────────────────────────────────────┤
    │ [VIDEO STREAM DETAILS]                                                                               │
    │ Dimensions 3840 × 2160 (4K UHD) [DIFF] 1920 × 1080 (1080p Full HD)                                   │
    │ Video Codec Apple ProRes 422 (apch) [DIFF] HEVC / H.265 (hvc1)                                       │
    │ Frame Rate 23.976 fps (Standard) [MATCH] 23.976 fps (Standard)                                       │
    │ Color Primaries ITU-R BT.2020 (HDR) [DIFF] ITU-R BT.709 (SDR)                                        │
    │ Transfer Function SMPTE ST 2084 (PQ HDR10) [DIFF] ITU-R BT.709                                       │
    │ Bit Depth 10-bit [MATCH] 10-bit                                                                      │
    │ Chroma Subsampling 4:2:2 [DIFF] 4:2:0                                                                │
    │ Duration 00:02:14.500 [DIFF] 00:02:14.583 (Drift: +2 frames)                                         │
    └──────────────────────────────────────────────────────────────────────────────────────────────────────┘

## 📖 The Product Story

### *Why we built VideoPeek*

In digital cinema, broadcast mastering, color grading, and streaming delivery, video workflows are more complex than ever:

* **Color space confusion:** Did your render preserve wide-gamut **ITU-R BT.2020** HDR10, or was it quietly clamped to standard **Rec.709** SDR?
* **Chroma subsampling drops:** Did your mastering transcode maintain **10-bit 4:2:2** master fidelity, or was it degraded to **8-bit 4:2:0**?
* **Frame rate pull-downs & drift:** Did an automated web pipeline drop 2 frames or introduce a 23.976 $\rightarrow$ 29.97 fps pulldown stutter?
* **Bloated tooling:** Opening DaVinci Resolve or Final Cut Pro just to check a video's transfer function (EOTF) or FourCC codec takes 30 seconds. QuickTime Player's basic inspector hides crucial mastering data, and terminal tools like `ffprobe` disrupt your creative flow.

We asked a simple question: **What if you had a blazing-fast, visually pristine Mac app that reveals the complete DNA of any video file in under 200 milliseconds?**

VideoPeek was created to answer that need. Built from the ground up in 100% native Swift and SwiftUI, VideoPeek taps directly into Apple’s low-level `CoreMedia`, `AVFoundation`, `VideoToolbox`, and `CryptoKit` frameworks. No web runtimes. No GPU memory exhaustion. Just pure, instant video intelligence.


## ⚡ Key Features

<table width="100%">
  <tr>
    <td width="50%" valign="top">
      <h3>🎞️ Deep Visual Bitstream Demuxing</h3>
      <p>Inspect true FourCC codec tags (<code>apch</code>, <code>hvc1</code>, <code>avc1</code>, <code>av01</code>), native dimensions, aspect ratios, clean aperture, scan types, and frame counts without decoding heavy video frames into VRAM.</p>
    </td>
    <td width="50%" valign="top">
      <h3>⚖️ Side-by-Side A-B Video Comparator</h3>
      <p>Compare two video files simultaneously. VideoPeek aligns property keys and instantly highlights resolution scaling, color gamut drops, chroma downgrades, and missing audio tracks.</p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>⏱️ Frame-Accurate Drift & Timecode Analytics</h3>
      <p>Detect exact frame drops (<code>+2 frames</code>) and millisecond duration discrepancies (down to 0.1ms) between mastering masters and compressed web transcode generations.</p>
    </td>
    <td width="50%" valign="top">
      <h3>🎨 Color Primaries, HDR & EOTF Profiling</h3>
      <p>Instantly extract Color Primaries (BT.709, BT.2020, DCI-P3), Transfer Characteristics (SDR, SMPTE ST 2084 / PQ HDR10, ARIB STD-B67 / HLG, Apple Log), and YCbCr matrix coefficients.</p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>🛡️ Hardware-Accelerated SHA-256</h3>
      <p>Stream massive 100+ GB ProRes or camera raw masters in 64 KB binary chunks through Apple Silicon’s hardware cryptographic engine without memory bloat.</p>
    </td>
    <td width="50%" valign="top">
      <h3>🔤 Scoped Report Font Zoom</h3>
      <p>Adjust the reporting table’s typography independently (<code>A-</code> / <code>A+</code> / <code>↺ Reset</code>). Scale the specification tree without breaking your window layout or toolbar chrome.</p>
    </td>
  </tr>
</table>

## 🎯 Universal Container & Codec Support

VideoPeek parses uncompressed cinema masters, broadcast containers, and web streams:

| Category | Supported Containers & Codecs |
| :--- | :--- |
| **Cinema & Post-Production** | **Apple ProRes Family** (ProRes 422 HQ, 422, LT, Proxy, 4444, 4444 XQ in `.mov`), **Apple ProRes RAW** |
| **Modern Web & Streaming** | **HEVC / H.265** (Main 10, HDR10, Dolby Vision), **H.264 / AVC** (High, Main, Baseline), **AV1** (`.mp4`, `.mkv`, `.webm`) |
| **Broadcast & Archival** | **Broadcast MXF** (`.mxf`), **MPEG Transport Stream** (`.ts`, `.mts`, `.m2ts`), **Audio Video Interleave** (`.avi`), **Matroska** (`.mkv`) |
| **Embedded Audio Streams** | **Linear PCM** (24/32-bit Multi-Channel), **AAC-LC**, **Dolby Digital (AC-3)**, **Dolby Digital Plus (E-AC-3)**, **ALAC**, **FLAC** |
| **Subtitles & Timecodes** | **SMPTE Timecode Tracks**, **CEA-608 / CEA-708 Closed Captions**, **TX3G**, **WebVTT** |


## 🏆 Why VideoPeek is Different

Most diagnostic utilities are bloated ports. VideoPeek is built exclusively for macOS:

<div style="overflow-x: auto; margin: 24px 0;">
  <table style="width: 100%; border-collapse: collapse; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; font-size: 0.9rem; text-align: left; border: 1px solid rgba(128,128,128,0.25); border-radius: 8px; overflow: hidden;">
    <thead>
      <tr style="background: rgba(128,128,128,0.1); border-bottom: 2px solid rgba(128,128,128,0.25);">
        <th style="padding: 12px 16px; width: 30%;">Capability / Metric</th>
        <th style="padding: 12px 16px; width: 25%; background: rgba(0, 113, 227, 0.08); color: #0071e3; font-weight: 700;">VideoPeek</th>
        <th style="padding: 12px 16px; width: 25%;">MediaInfo (GUI)</th>
        <th style="padding: 12px 16px; width: 20%;">ffprobe (CLI)</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15);">
        <td style="padding: 10px 16px; font-weight: 600;">Native Architecture</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">✅ 100% Swift / CoreMedia</td>
        <td style="padding: 10px 16px;">⚠️ WxWidgets Port</td>
        <td style="padding: 10px 16px;">⚠️ C Utility</td>
      </tr>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15); background: rgba(128,128,128,0.02);">
        <td style="padding: 10px 16px; font-weight: 600;">Launch Time</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">⚡ &lt; 10 ms (Instant)</td>
        <td style="padding: 10px 16px;">🐢 800+ ms</td>
        <td style="padding: 10px 16px;">⚡ Fast</td>
      </tr>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15);">
        <td style="padding: 10px 16px; font-weight: 600;">Memory Footprint</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">🪶 ~ 24 MB (No VRAM Buffer)</td>
        <td style="padding: 10px 16px;">🐘 120 MB</td>
        <td style="padding: 10px 16px;">🪶 ~ 20 MB</td>
      </tr>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15); background: rgba(128,128,128,0.02);">
        <td style="padding: 10px 16px; font-weight: 600;">Visual A-B Diff Mode</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">✅ Built-in Split-Table</td>
        <td style="padding: 10px 16px;">❌ None</td>
        <td style="padding: 10px 16px;">❌ Manual diff</td>
      </tr>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15);">
        <td style="padding: 10px 16px; font-weight: 600;">Frame Drift Analytics</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">✅ Exact (ΔFrames &amp; Δt)</td>
        <td style="padding: 10px 16px;">❌ None</td>
        <td style="padding: 10px 16px;">❌ Manual math</td>
      </tr>
      <tr style="border-bottom: 1px solid rgba(128,128,128,0.15); background: rgba(128,128,128,0.02);">
        <td style="padding: 10px 16px; font-weight: 600;">120Hz ProMotion UI</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">✅ Liquid Smooth</td>
        <td style="padding: 10px 16px;">❌ Frame drops</td>
        <td style="padding: 10px 16px;">❌ Terminal only</td>
      </tr>
      <tr>
        <td style="padding: 10px 16px; font-weight: 600;">Hardware SHA-256</td>
        <td style="padding: 10px 16px; background: rgba(0, 113, 227, 0.04); font-weight: 600;">✅ CryptoKit NEON Engine</td>
        <td style="padding: 10px 16px;">❌ Not included</td>
        <td style="padding: 10px 16px;">⚠️ Separate tool</td>
      </tr>
    </tbody>
  </table>
</div>


## ✨ User Experience Highlights

### 1. Dual-Drop Compare Mode
Select two video files in Finder (like your 4K ProRes master and your 1080p H.265 YouTube render) and drag them together onto VideoPeek. The window instantly transitions into a **two-column comparative diff table**, highlighting mismatches in bold amber and identical parameters in calm green.

### 2. Zero VRAM Exhaustion on Massive Master Files
Thanks to non-blocking stream demuxing, dropping a **120 GB ProRes 4444 XQ feature film master** takes the exact same fraction of a second as opening a **15 MB MP4 screen recording**.

### 3. Native Mac Ergonomics
* Full support for macOS Dark and Light modes.
* Universal keyboard shortcuts (`⌘O` to open, `⌘E` to export, `⌘C` to copy, `⌘+` to scale text, `⇧⌘L` to view logs).
* Multi-column search bar that filters video keys, codecs, and color properties instantly as you type.



## 🚀 Elevate Your Video Mastering & QC Workflow

Stop guessing what is inside your video containers. Verify color gamuts, confirm chroma subsampling, and validate frame-rate parity with pixel-perfect precision.


## 💬 Help & Support

### Frequently Asked Questions

<details>
<summary><strong>Does VideoPeek alter or re-encode my video files?</strong></summary>
<p>No. VideoPeek operates strictly in read-only mode. It inspects container headers and stream format descriptions without modifying or re-encoding a single frame of your footage.</p>
</details>

<details>
<summary><strong>Where are diagnostic logs stored?</strong></summary>
<p>VideoPeek maintains rolling daily logs formatted as <code>videopeek-YYYY-MM-DD.log</code>. You can reveal your log folder directly in Finder anytime by pressing <code>⇧ + ⌘ + L</code> (or via <strong>Help → Show Logs in Finder</strong>).</p>
</details>

<details>
<summary><strong>Is VideoPeek private?</strong></summary>
<p>Yes. VideoPeek is 100% secure. It contains zero analytics, no telemetry, no tracking, and never makes unauthorized network connections.</p>
</details>

<details>
<summary><strong>How do I report a bug or request a new container format?</strong></summary>
<p>You can open an issue or start a discussion on our official <a href="https://github.com/barshasantak/VideoPeek/issues">GitHub Issues page</a>.</p>
</details>


### Support

You can report any issues here: [https://github.com/barshasantak/videopeek/issues](https://github.com/barshasantak/videopeek/issues){:target="_blank"}

 <br>
 
 <hr>
   <small>© 2026 Santak Das, Tara Design Studio. All rights reserved.</small>
 <br>

