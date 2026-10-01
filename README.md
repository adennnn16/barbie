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
    A high-precision quality control application built to inspect Barbie packaging integrity in real-time. Combines <b>FastAPI + OpenCV (SIFT Feature Matching)</b> with continuous <b>WebSocket streaming</b>, external hardware camera integration, and robust enterprise-grade <b>anti-screenshot security</b>.
  </p>

</div>

---

## 📸 App Preview & Hardware Setup

| 📱 Live Scanner Interface | 🔒 Anti-Screenshot Defense | 📷 Hardware & Microcontroller Setup |
| :---: | :---: | :---: |
| <img width="585" height="1266" alt="Image" src="https://github.com/user-attachments/assets/ba047895-2723-45fb-8e3f-91802e2d75b9" /> | <img width="585" height="1266" alt="Image" src="https://github.com/user-attachments/assets/4fbab3d1-f4a0-47d6-bf51-ee180db56c02" /> | <img width="1169" height="1418" alt="Image" src="https://github.com/user-attachments/assets/62dbee10-af60-4b21-b50e-48c6d8a0a900" />|
| **Main Inspection Interface**<br>Interactive web interface showing real-time video feed frame, reference upload button, and scanning triggers. | **Copyright & DRM Overlay**<br>Active screen protection layer that automatically hides sensitive inspection data when screenshot/recording is detected. | **Inspection Hardware**<br>Compact USB camera setup interfaced with laptop workstation & Arduino microcontroller for physical factory line integration. |

---

## ✨ Key Features

- **🎯 One-Shot Master Reference Matching:** Upload a single pristine standard photo as the master reference image.
- **⚡ Continuous Real-Time Inspection:** Websocket-driven frame streaming at ~300ms intervals using OpenCV SIFT feature extraction.
- **🛡️ Enterprise Multi-Layer Security:**
  - **Native Android Security (`FLAG_SECURE`):** Completely blocks screen captures, recording, and app switcher previews.
  - **Browser DRM Protection:** Dynamic overlay warning ("PROTECTED SCREEN") preventing unauthorized screenshots, page prints (`Ctrl+P`), or screen recordings.
- **🔌 Hardware Integration:** External webcam module linked with Python OpenCV backend and microcontroller board for automated defect physical signal triggers.
- **💄 Barbie Signature Aesthetic:** Custom pink-themed user interface matching Mattel Barbie branding guidelines.

---

## 🤖 Computer Vision & Inspection Pipeline

Unlike conventional deep learning classifiers that require thousands of labeled training images, this system employs **Scale-Invariant Feature Transform (SIFT)** paired with **k-Nearest Neighbors (k-NN) Feature Matching** for instant, scale- and rotation-invariant packaging inspection.

```text
┌─────────────────┐     ┌──────────────────────┐     ┌──────────────────────┐
│ Master Reference│───> │ SIFT Keypoints       │───┐ │                      │
│ Packaging Image │     │ & 128-dim Descriptors│   │ │ FLANN / BFMatcher    │     ┌──────────────────┐
└─────────────────┘     └──────────────────────┘   ├─>│ k-NN Ratio Match     │────>│ Quality Score    │
                                                   │ │ (Lowe's Ratio Test)  │     │ & Pass/Fail Status│
┌─────────────────┐     ┌──────────────────────┐   │ │                      │     └──────────────────┘
│ Live Camera     │───> │ SIFT Keypoints       │───┘ └──────────────────────┘
│ Video Frame     │     │ & 128-dim Descriptors│
└─────────────────┘     └──────────────────────┘
