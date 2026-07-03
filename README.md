# ESP32-CAM YOLO Edge AI Detection System

A real-time industrial pipe clamp detection system using ESP32-CAM and YOLOv8.

This project utilizes an ESP32-CAM module to capture images and stream them over WiFi. The captured frames are processed by a custom-trained YOLOv8 model running on a computer to detect pipe clamps in real time.

---

## Features

- Real-time image capture using ESP32-CAM
- Custom-trained YOLOv8 object detection model
- Pipe clamp detection
- Image and video inference
- OpenCV-based visualization
- WiFi-based communication
- Lightweight edge AI architecture
- Industrial inspection and monitoring applications

---

## System Architecture

```text
ESP32-CAM
     │
     ▼
WiFi Image Streaming
     │
     ▼
Python Application
(OpenCV + Requests)
     │
     ▼
YOLOv8 Inference Engine
     │
     ▼
Clamp Detection
     │
     ▼
Bounding Box Visualization
```

---

## Technologies Used

- Python
- YOLOv8 (Ultralytics)
- OpenCV
- ESP32-CAM
- Arduino IDE
- NumPy
- Requests
- Roboflow

---

## Hardware Requirements

- ESP32-CAM (AI Thinker)
- WiFi Network
- Laptop / PC
- Industrial Pipe Clamp Dataset

---

## Software Requirements

Install required Python libraries:

```bash
pip install ultralytics opencv-python numpy requests
```

Verify YOLO installation:

```bash
yolo
```

---

## Workflow

```text
Dataset Collection
        │
        ▼
Roboflow Annotation
        │
        ▼
YOLOv8 Training
        │
        ▼
best.pt Model Generation
        │
        ▼
ESP32-CAM Image Capture
        │
        ▼
WiFi Transmission
        │
        ▼
YOLOv8 Inference
        │
        ▼
Pipe Clamp Detection
```

---

## Detection Classes

| Class |
|---------|
| clamp |

---

## Model Performance

| Metric | Value |
|----------|----------|
| Precision | 0.97 |
| Recall | 0.90 |
| mAP@50 | 0.94 |
| mAP@50-95 | 0.75 |

---

## Applications

- Industrial Pipeline Inspection
- Automated Maintenance Monitoring
- Smart Manufacturing
- Asset Tracking
- Industrial Safety Systems
