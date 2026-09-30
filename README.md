<div align="center">

  <!-- Official SVG Brand Logos -->
  <p align="center">
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/00/Mattel_logo.svg" alt="Mattel Logo" height="65" />
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/0b/Barbie_Logo.svg" alt="Barbie Logo" height="65" />
  </p>

  # Barbie™ Packaging Inspector
  ### *Real-Time Automated Packaging Defect Detection & Anti-Screenshot System*

  [![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
  [![OpenCV](https://img.shields.io/badge/OpenCV-Computer_Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org)
  [![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.0-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com)
  [![Security](https://img.shields.io/badge/Security-FLAG__SECURE-E0115F?style=for-the-badge&logo=android&logoColor=white)](#-multi-layer-security-architecture)

  <p align="center">
    A high-precision quality control application built to inspect Barbie packaging integrity in real-time. Combines <b>FastAPI + OpenCV (SIFT Feature Matching)</b> with continuous <b>WebSocket streaming</b> and robust enterprise-grade <b>anti-screenshot security</b>.
  </p>

</div>

---

## 📸 App Preview & Interface

| 🎥 Live Camera Scanner | 🔒 Anti-Screenshot Blackout |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x600/0f0f10/e0115f?text=Live+Scanner+UI" width="300" alt="Live Scanner UI" /> | <img src="https://via.placeholder.com/400x600/000000/e0115f?text=Screenshot+Blocked" width="300" alt="Anti Screenshot Blocked" /> |
| *Real-time visual comparison & score analysis* | *Instant screen blackout on capture/tab switch* |

---

## ✨ Key Features

- **🎯 One-Shot Master Reference Matching:** Upload a single pristine standard photo as the master reference image.
- **⚡ Continuous Real-Time Inspection:** Websocket-driven frame streaming at ~300ms intervals using OpenCV SIFT feature extraction.
- **🛡️ Enterprise Multi-Layer Security:**
  - **Native Android Security (`FLAG_SECURE`):** Completely blocks screen captures, recording, and app switcher previews (outputs a 100% black screen).
  - **Browser-Level Defense:** Real-time canvas blur on window blur/tab switch, DevTools blocking, and keybind prevention (`PrintScreen`, `Ctrl+P`, `F12`).
  - **IP Whitelisting:** Restricted access via Nginx Reverse Proxy rules.
- **💄 Barbie Signature Aesthetic:** Custom dark-mode UI with Barbie-pink accents, pulse indicators, and dynamic match status feeds.

---

## 🏗️ System Architecture & Tech Stack

```text
┌───────────────────────────────────────────────────────────────────────────┐
│                             CLIENT LAYER                                  │
│                 (Capacitor / Android Webview Wrapper)                     │
│                                                                           │
│   • HTML5 Camera Stream (300ms Interval)  • Tailwind CSS Dark Theme       │
│   • Canvas Blur on Window Blur            • Android FLAG_SECURE Engine    │
└─────────────────────────────────────┬─────────────────────────────────────┘
                                      │
                                      │ WSS / HTTP REST
                                      ▼
┌───────────────────────────────────────────────────────────────────────────┐
│                       PROXY & SECURITY GATEWAY                            │
│                         (Nginx Reverse Proxy)                             │
│                                                                           │
│   • IP Whitelisting Subnet Filter         • SSL / TLS Encryption          │
│   • WebSocket Upgrade Proxying            • Rate Limiting                 │
└─────────────────────────────────────┬─────────────────────────────────────┘
                                      │
                                      │ Internal Forwarding
                                      ▼
┌───────────────────────────────────────────────────────────────────────────┐
│                           BACKEND AI ENGINE                               │
│                           (FastAPI Server)                                │
│                                                                           │
│   • WebSocket Frame Ingestion             • NumPy Matrix Processing       │
│   • OpenCV SIFT Feature Matcher           • Flann / BFMatcher Scoring     │
└───────────────────────────────────────────────────────────────────────────┘
