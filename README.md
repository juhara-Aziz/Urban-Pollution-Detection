# Visual Pollution Detection — Saudi Public Roads

#### An object detection system that processes video footage from municipal patrol vehicles and automatically detects, tracks, and counts visual pollution elements on public roads — replacing manual inspection with an automated pipeline.

#### Built on YOLO11n, trained on a labeled subset of the Saudi Arabia Public Roads Visual Pollution Dataset.

## Problem & Objective

#### Municipal vehicles in Saudi Arabia capture road footage to document visual pollution, but reviewing this footage has traditionally relied on manual inspection through a government-managed reporting app — slow, inconsistent, and unable to scale with the volume of footage collected nationwide.

#### This project automates that process: given a video input, the system detects each visual pollution element frame-by-frame, tracks it across frames to avoid duplicate counting, and outputs a structured summary of object counts per class.

### Detected classes:

####  Excavation Barriers
#### Potholes
#### Dilapidated Sidewalks

## Dataset

### Source	Saudi Arabia Public Roads Visual Pollution Dataset (Mendeley Data)
### Collected by	Ministry of Municipal and Rural Affairs and Housing (MOMRAH), Saudi Arabia
### Original size	31,795 images
### Subset used	9,000 images (random sample, seed=42)
### Split	7,200 train / 900 validation / 900 test
### Format	YOLO (.txt annotations)

