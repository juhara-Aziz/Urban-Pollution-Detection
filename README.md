# Visual Pollution Detection — Saudi Public Roads

An AI-powered computer vision system for automatically detecting visual pollution and road-related problems in Saudi public roads using video footage.

The system uses **YOLO11n** to detect road problems frame-by-frame and provides structured detection results including object class, confidence score, and bounding box information. A prototype severity and priority scoring system is also used to estimate the urgency of maintenance based on the detected problem type, object size, and model confidence.

---

## Problem & Objective

Municipal and road inspection teams collect large amounts of road footage to monitor public infrastructure and identify visual pollution and road-related problems.

Manual inspection of this footage can be time-consuming and difficult to scale as the volume of collected videos increases.

This project aims to automate the initial inspection process by using computer vision to:

- Detect road-related problems automatically from images and videos.
- Identify the type of detected problem.
- Estimate the confidence of each detection.
- Analyze the relative size of detected objects.
- Estimate a severity score for detected problems.
- Assign a maintenance priority level.
- Generate structured results that can support road inspection and maintenance decisions.

---

## Detected Classes

The current model detects three road-related classes:

| Class | Description |
|---|---|
| `barriers` | Excavation barriers |
| `pothole` | Potholes and road surface damage |
| `sidewalks` | Dilapidated or damaged sidewalks |

---

## System Pipeline

The overall pipeline is:

```text
Road Video
     │
     ▼
YOLO11n Object Detection
     │
     ├── Class
     ├── Confidence
     └── Bounding Box
     │
     ▼
Detection Analysis
     │
     ├── Object Size
     └── Detection Frequency
     │
     ▼
Severity Scoring
     │
     ▼
Priority Level
     │
     ▼
Road Condition Assessment
