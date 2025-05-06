# Deep-learning-project-group13-COD-Mega_detector
# Big Cat Detection & Classification in Camera Trap Imagery


A computer vision system for detecting and classifying big cats in camera trap imagery, with enhanced performance on camouflaged animals through dataset augmentation and model improvements.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Objectives](#key-objectives)
- [Datasets](#datasets)
- [Methodology](#methodology)
- [Deliverables](#deliverables)


## Project Overview
This project aims to improve wildlife detection systems with special focus on big cats (lions, tigers, leopards, cheetahs) in camera trap imagery. Originally targeting snow leopards, we expanded our scope due to data scarcity. Our work focuses on:

- Evaluating and improving MegaDetector's performance on camouflaged animals
- Leveraging specialized datasets (COD10K)
- Improving Mega detector v6 for camouflaged object detection.

## Key Objectives
1. Evaluate SOTA MegaDetector performance on camouflaged wildlife
2. improve SOTA MegaDetector performance on camouflaged wildlife
3. Combine empty/non-empty cam/noncam for improved training
4. finetune with camouflage-oriented datasets (COD10K)
5. Using/training YOLOv9-based detection system using MegaDetector

## Datasets

### COD10K Dataset
- **10,000 images** with segmentation masks & object boundaries
- **69 classes** including 4 big cat species
- Focus on **camouflaged objects**
- **Strengths**: Detailed annotations, camouflage focus, Exisiting bounding box documentations
- **Limitations**: Sparse big cat samples, aquatic species noise

### LILA MetaDataset
- Aggregates **7.1M+ camera trap images**
- Key components:
  - Snapshot Serengeti (16605 lion images)
  - Multiple other wildlife datasets
- **Strengths**: Real-world camera trap diversity
- **Limitations**: Sparse bounding box annotations, sparsely labeled camouflaged imagery

## Methodology

1. **Data Curation**
   - Filter aquatic/non-relevant classes
   - Filter coco-json file (to put data in trainable format)
   - Made yolo label .txt file using the existing coco JSON file (to put data in trainable format) 
   - Combine empty/non-empty images (empty yolo labels for empty images)

2. **Model Architecture**
   - YOLOv9-e baseline
   - MegaDetector v6 integration

3. **Evaluation Metrics**
   - True positive count
   - Intersection over Union (IoU)
   - Confidence score analysis

## Deliverables

### Deliverable 2: Dataset Analysis
- COD10K contains 4 big cat classes but limited samples
- LILA's Snapshot Serengeti has 23,822 big cat images
- Key challenge: Only 31% of LILA datasets include bounding boxes

### Deliverable 3: MegaDetector Evaluation
- **41%** correct animal detection on COD10K
- Confidence scores (mean: 0.5133 ± 0.2385)
- **18.7%** high-confidence detections (≥0.8)
- **40%** complete detection failures
- **0.256** mean IOU score

### Deliverable 4: Data Preparation
- Custom COCO JSON/YOLO TXT conversion
- Class mapping:
  - `0`: Animal
  - `1`: Human
- Train/Test/Val split: 70/20/10


### Deliverable 5/6: Model Training and results
- Mega detector (YOLOv9-e) trained for 40 epochs
- Hyperparameters:
  lr0: 0.001
  batch: 16
  imgsz: 512
- Results: 
    IoU Improvement: 0.256 → 0.281 (+9.7%)
    box loss Improvement: 1.8 -> 1.4
    as well as improving the cls and dfl loss