# Vision Trace: Project Report

## Executive Summary

Vision Trace is an intelligent traffic anomalies and smart city video surveillance network designed to address the problem of delayed emergency response to traffic incidents. The system provides real-time monitoring of camera feeds, performs vehicle detection and tracking, and generates instant alerts for vehicle accidents and stalls.

## Problem Statement

City traffic operations currently rely on manual review of camera networks to identify vehicle accidents, stalls, or public safety obstructions. This manual process drastically delays emergency team deployment, potentially putting lives at risk and increasing traffic congestion.

## Solution Overview

Vision Trace is a full-stack AI solution consisting of three main components:

1. **AI Layer**: Object detection and tracking
2. **Backend & Database**: High-frequency processing pipeline
3. **UI Command Center**: Real-time monitoring and alerting interface

## System Architecture

### 1. AI Layer
- **Object Detection**: Fine-tuned YOLOv8 (nano version for speed) to localize vehicles
  - Detects: cars, motorcycles, buses, trucks
- **Object Tracking**: DeepSORT algorithm to assign constant identity IDs across frames
- **Anomaly Detection**:
  - Sudden speed variations to detect stalls
  - Vector collision and bounding box overlap to detect accidents

### 2. Backend & Database
- **Framework**: Flask (Python)
- **Processing Pipeline**: High-frequency frame-by-frame analysis
- **Database**: MongoDB (placeholder integration) for storing event tracking objects and alerts
- **Features**:
  - Lane density level measurement
  - Instantaneous event tracking
  - Alert generation and persistence

### 3. UI (HTML/CSS/JS)
- **Layout**: Modern command center grid
- **Features**:
  - Live streaming canvas blocks
  - Dynamic overlays pointing at tracked vehicles
  - Reactive alert banners with on-screen warnings
  - Sound notifications for alerts

## Implementation Details

### Backend (`backend/app.py`)
- Flask server with CORS enabled
- YOLOv8 model from Ultralytics
- DeepSORT tracker from deep-sort-realtime library
- Vehicle speed calculation based on position changes over time
- Collision detection via bounding box overlap
- Alert generation with timestamps

### Frontend
- **index.html**: Main page structure with video feed, canvas overlay, stats, and alerts section
- **style.css**: Dark-themed gradient UI with responsive design
- **app.js**: Frontend logic to communicate with backend, update UI, and play alert sounds

## Project Structure

```
vision trace/
├── backend/
│   └── app.py
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── app.js
├── requirements.txt
├── README.md
└── PROJECT_REPORT.md
```

## Setup & Installation

### Prerequisites
- Python 3.7+
- pip

### Installation Steps

1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

2. **Start Backend**
   ```bash
   cd backend
   python app.py
   ```

3. **Open Frontend**
   - Open `frontend/index.html` in a web browser

## Usage

1. Click "Start Monitoring" button in the UI
2. The system will begin processing video frames
3. Detected vehicles will be counted and tracked
4. When an anomaly (stall or collision) is detected, an alert will appear in the alerts feed with a sound notification

## Future Enhancements

- Multiple camera support
- WebSocket integration for real-time data streaming
- Complete MongoDB persistence
- Historical alert analytics
- User authentication and authorization
- Integration with emergency services dispatch systems
- More sophisticated anomaly detection algorithms

## Conclusion

Vision Trace provides an automated, AI-powered solution to traffic incident detection, significantly reducing emergency response times and improving public safety in urban environments.
