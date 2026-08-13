# Visual Pollution Detection — Saudi Public Roads

An object detection system that processes video footage from municipal patrol vehicles and automatically detects visual pollution elements on public roads.

Built on **YOLO11n**, trained on a labeled subset of the [Saudi Arabia Public Roads Visual Pollution Dataset](https://data.mendeley.com/datasets/bb7b8vtwry).

The system detects road-related problems frame-by-frame and provides structured detection results that can be used for further analysis, severity estimation, and maintenance prioritization.

---

##  Problem & Objective

Municipal vehicles in Saudi Arabia capture road footage to document visual pollution and road-related problems. Reviewing large volumes of video footage manually can be time-consuming, inconsistent, and difficult to scale.

This project aims to automate the initial inspection process.

Given a road video as input, the system:

- Detects visual pollution elements frame-by-frame.
- Identifies the detected problem class.
- Provides a confidence score for each detection.
- Extracts bounding box information.
- Analyzes the detected objects based on their relative size.
- Estimates a severity score.
- Assigns a maintenance priority level.

### Detected Classes

-  Excavation Barriers
-  Potholes
-  Dilapidated Sidewalks

---

## 📊 Dataset

| Property | Description |
|---|---|
| **Source** | [Saudi Arabia Public Roads Visual Pollution Dataset](https://data.mendeley.com/datasets/bb7b8vtwry) |
| **Collected by** | Ministry of Municipal and Rural Affairs and Housing (MOMRAH), Saudi Arabia |
| **Original size** | 31,795 images |
| **Subset used** | 9,000 images |
| **Sampling** | Random sample, seed = 42 |
| **Split** | 7,200 train / 900 validation / 900 test |
| **Format** | YOLO (`.txt` annotations) |

The selected subset contains **11,741 object annotations** across the three target classes.

---
## Notebook Pipeline


| Section                                   | Description                                                  |
| ----------------------------------------- | ------------------------------------------------------------ |
| **01 — Project Overview**                 | Problem statement, objective, and project scope              |
| **02 — Environment Setup**                | Dependency installation and GPU check                        |
| **03 — Path Configuration**               | Dataset and directory configuration                          |
| **04 — Dataset Selection**                | Random 9,000-image subsampling                               |
| **05 — Data Extraction**                  | Extracting selected images and labels                        |
| **06 — Dataset Preparation & Validation** | Dataset integrity checks and `data.yaml` creation            |
| **07 — Exploratory Data Analysis**        | Class distribution and bounding box analysis                 |
| **08 — Baseline Model**                   | YOLO11n training and evaluation                              |
| **09 — Inference on Images/Videos**       | Model inference and video-based detection                    |
| **10 — Severity & Priority Scoring**      | Detection-based severity and maintenance priority estimation |

---

##  Model Architecture & Training Configuration

The baseline model was built using **YOLO11n (YOLO11 Nano)**, a lightweight object detection architecture selected as a baseline due to its relatively small computational footprint and suitability for real-time inference.

### Training Configuration

| Parameter | Value |
|---|---:|
| **Epochs** | 50 |
| **Image Size** | 640 × 640 |
| **Batch Size** | 16 |
| **Training Images** | 7,200 |
| **Validation Images** | 900 |
| **Test Images** | 900 |
| **Classes** | 3 |

### Model Classes

```text
0 → barriers
1 → sidewalks
2 → pothole

---

## Baseline Results

The YOLO11n baseline was evaluated on the held-out test set containing 900 images and 1,183 object instances.

Overall Performance
| Metric    |     Score |
| --------- | --------: |
| Precision | **0.583** |
| Recall    | **0.595** |
| mAP50     | **0.601** |
| mAP50-95  | **0.360** |

Per-Class Performance
| Class     |     mAP50 |  mAP50-95 |
| --------- | --------: | --------: |
| Pothole   | **0.714** | **0.437** |
| Sidewalks | **0.614** | **0.326** |
| Barriers  | **0.474** | **0.317** |

###Key Finding
The pothole class achieved the strongest detection performance, while barriers achieved the lowest mAP50.
This is consistent with the exploratory analysis: potholes represent the majority of annotations, while barriers are less represented and have considerably smaller bounding boxes.

---

##Technologies

Python
YOLO11n
Ultralytics
PyTorch
OpenCV
Pandas
NumPy
Matplotlib


---

##Conclusion

This project demonstrates an end-to-end computer vision pipeline for detecting visual pollution and road-related problems in Saudi public roads.

The YOLO11n baseline achieved:

60.1% mAP50
36.0% mAP50-95
58.3% Precision
59.5% Recall

The results establish a baseline for future model improvements, while the severity and priority scoring layer extends the system from object detection toward automated road-condition assessment and maintenance decision support.


---

## Project Team

This project was developed by:

- **Aljuhara**
- **Maram**
- **Saleh**
- **Sultan**

---
