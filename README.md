# Deep-learning-project-group13-COD-Mega_detector
# Big Cat Detection & Classification in Camera Trap Imagery


A computer vision system for detecting and classifying big cats in camera trap imagery, with enhanced performance on camouflaged animals through dataset augmentation and model improvements.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Objectives](#key-objectives)
- [Datasets](#datasets)
- [Methodology](#methodology)
- [Deliverables](#deliverables)
- [Implementation](#implementation)
- [Results](#results)
- [Future Work](#future-work)
- [License](#license)

## Project Overview
This project aims to improve wildlife detection systems with special focus on big cats (lions, tigers, leopards, cheetahs) in camera trap imagery. Originally targeting snow leopards, we expanded our scope due to data scarcity. Our work focuses on:

- Evaluating and improving MegaDetector's performance on camouflaged animals
- Leveraging specialized datasets (COD10K and LILA)
- Developing robust detection models for conservation applications

## Key Objectives
1. Evaluate SOTA MegaDetector performance on camouflaged wildlife
2. Combine empty/non-empty camera trap images for improved training
3. Experiment with camouflage-oriented datasets (COD10K)
4. Implement YOLOv9-based detection system
5. Improve localization accuracy through boundary learning

## Datasets

### COD10K Dataset
- **10,000 images** with segmentation masks & object boundaries
- **69 classes** including 4 big cat species
- Focus on **camouflaged objects**
- **Strengths**: Detailed annotations, camouflage focus
- **Limitations**: Sparse big cat samples, aquatic species noise

### LILA MetaDataset
- Aggregates **7.1M+ camera trap images**
- Key components:
  - Snapshot Serengeti (16605 lion images)
  - Multiple other wildlife datasets
- **Strengths**: Real-world camera trap diversity
- **Limitations**: Sparse bounding box annotations

## Methodology

![Workflow Diagram](https://via.placeholder.com/800x400.png?text=Project+Workflow)

1. **Data Curation**
   - Filter aquatic/non-relevant classes
   - Combine empty/non-empty images
   - Handle camouflage-specific challenges

2. **Model Architecture**
   - YOLOv9-e baseline
   - MegaDetector v6 integration
   - Boundary-aware detection heads

3. **Evaluation Metrics**
   - Intersection over Union (IoU)
   - Confidence score analysis
   - False positive rate assessment

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

### Deliverable 4/5: Data Preparation
- Custom COCO JSON/YOLO TXT conversion
- Class mapping:
  - `0`: Animal
  - `1`: Human
- Train/Test/Val split: 70/20/10

### Deliverable 6: Model Training
- YOLOv9-e trained for 40 epochs
- Hyperparameters:
  ```yaml
  lr0: 0.01
  weight_decay: 0.0005
  batch: 16
  imgsz: 640