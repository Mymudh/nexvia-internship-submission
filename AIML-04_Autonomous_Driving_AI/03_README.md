# Autonomous Driving AI (ADAS)

## Overview
A web-based road-scene perception prototype with a React/Vite dashboard and Flask API. Repository modules cover YOLO object detection, video analysis, ByteTrack object tracking, OpenCV lane detection, MiDaS relative depth, optional ENet lane segmentation, and CARLA/ROS 2 integration code.

## Links
- GitHub: https://github.com/Mymudh/autonomous-driving-ai
- Live application: https://adas-autonomous-driving.onrender.com/
- Dataset reference: https://www.kaggle.com/datasets/solesensei/solesensei_bdd100k?resource=download

## Technology
React, Vite, Flask, Python, Ultralytics YOLO, ByteTrack, OpenCV, MiDaS, PyTorch, ONNX, optional CARLA and ROS 2. TensorRT requires compatible NVIDIA hardware.

## Main modules
- Backend API and routes: `backend/`
- Frontend pages: `frontend/src/pages/`
- Model training and export: `model_training/`
- CARLA bridge and ROS 2 node: `simulation/`
- API/model docs: `docs/`

## Features represented in the interface
Dashboard/model status, image detection, video analysis, tracking, lane detection, depth estimation, driving simulation and project Q&A assistant. The supplied screenshots confirm these interface screens were shown; backend inference must be validated separately.

## Run locally
Use a compatible Python environment (Python 3.11 is recommended for dependency compatibility). From the project root:
```powershell
cd backend
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
python app.py
```
In a second terminal:
```powershell
cd frontend
npm install
npm run dev
```
Follow `backend/.env.example`, `docs/PROJECT_DOCUMENTATION.md` and root README for exact configuration.

## Model weights — critical
The YOLO checkpoint is expected at `backend/models/best.pt`. It was not included in the supplied source package. Detection, tracking and object-linked depth will not perform real YOLO inference until the correct trained checkpoint is added. Optional ENet lane segmentation requires its own checkpoint. MiDaS may download weights at runtime.

## Evaluation status
No validated mAP, precision, recall or repeatable FPS benchmark was included in the supplied source package. The simulation screenshot displays 61 FPS; treat that as a UI display, not a measured benchmark. Record real metrics from a validation run before reporting them.

## Hardware note
The reported laptop GPU is Intel UHD Graphics 620. It does not support NVIDIA CUDA/TensorRT acceleration. CPU inference can be tested locally; TensorRT must be evaluated on a compatible NVIDIA system.

## Evidence
See `08_Testing_Screenshots/`, `09_Demo_Video/`, and the PDF reports in this folder.
