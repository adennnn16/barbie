<div align="center">

  <!-- Logo / Header Badge -->
  <img src="https://img.shields.io/badge/MATTEL-Barbie-ff1493?style=for-the-badge&logo=barbie&logoColor=white" alt="Barbie Header" />
  
  # 💖 Barbie™ Packaging Inspector
  ### *Real-Time Automated Packaging Defect Detection & Anti-Screenshot Protection System*

  [![Python](https.img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688?style=flat-square&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
  [![OpenCV](https://img.shields.io/badge/OpenCV-Computer_Vision-5C3EE8?style=flat-square&logo=opencv&logoColor=white)](https://opencv.org)
  [![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.0-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com)
  [![Security](https://img.shields.io/badge/Security-FLAG__SECURE-ff1493?style=flat-square&logo=android&logoColor=white)](#-multi-layer-security-architecture)

  <p align="center">
    A high-precision quality control application built to inspect Barbie packaging integrity in real-time. Combines <b>FastAPI + OpenCV (SIFT Feature Matching)</b> with continuous <b>WebSocket streaming</b> and robust enterprise-grade <b>anti-screenshot security</b>.
  </p>

</div>

---

## 📸 App Preview & Interface

| 🎥 Live Camera Scanner | 🔒 Anti-Screenshot Blackout |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x600/0f0f10/ff1493?text=Live+Scanner+UI" width="300" alt="Live Scanner UI" /> | <img src="https://via.placeholder.com/400x600/000000/ff1493?text=Screenshot+Blocked" width="300" alt="Anti Screenshot Blocked" /> |
| *Real-time visual comparison & score analysis* | *Instant screen blackout on capture/tab switch* |

---

## ✨ Key Features

- **🎯 One-Shot Master Reference Matching:** Upload a single pristine standard photo as the master reference image.
- **⚡ Continuous Real-Time Inspection:** Websocket-driven frame streaming at ~300ms intervals using OpenCV SIFT feature extraction.
- **🛡️ Enterprise Multi-Layer Security:**
  - **Native Android Security (`FLAG_SECURE`):** Completely blocks screen captures, recording, and app switcher previews (outputs a 100% black screen).
  - **Browser-Level Defense:** Real-time canvas blur on window blur/tab switch, DevTools blocking, and keybind prevention (`PrintScreen`, `Ctrl+P`, `F12`).
  - **IP Whitelisting:** Restricted access via Nginx Reverse Proxy rules.
- **💄 Barbie Cyberpunk Aesthetic:** Custom dark-mode UI with Barbie-pink accents, pulse indicators, and dynamic match status feeds.

---

## 🛠️ Tech Stack & Architecture

```text
┌────────────────────────────────────────────────────────────────────────┐
│                          CLIENT LAYER (Mobile / PWA)                   │
│  • HTML5 Webcam Stream         • Tailwind CSS Custom Theme             │
│  • Anti-Screenshot Listeners    • Capacitor / Android Native Wrapper    │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │  WebSockets (ws://) / HTTP POST
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        PROXY & SECURITY LAYER                          │
│  • Nginx Reverse Proxy          • IP Whitelisting Rules                 │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                         BACKEND & AI LAYER                             │
│  • FastAPI (Python)            • OpenCV SIFT (Feature Matching)        │
│  • WebSockets Engine           • NumPy Image Processing                │
└────────────────────────────────────────────────────────────────────────┘
