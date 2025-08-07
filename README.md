
# High-Quality Segmentation for Improved Multi-Label Classification of Fundus Images

**Author**: Islem Chaari  
**Date**: August 2025


## 1. Overview

This project presents a deep learning framework for the automated classification of ocular diseases from retinal fundus images. The novelty lies in combining anatomical segmentation (via HQ-SAM) with ResNet-based classification enhanced by structural biomarkers.

### Main Objectives
- Segment the optic disc and cup using HQ-SAM fine-tuned for medical imaging.
- Extract clinically relevant biomarkers (e.g., cup-to-disc ratio, rim thickness).
- Improve disease prediction using a multimodal ResNet50 classifier.


## 2. Repository Structure


notebooks/ # Jupyter notebooks for preprocessing, training, evaluation
 segmentation/ # HQ-SAM fine-tuning and segmentation scripts
 classification/ # ResNet50 classifier with biomarker integration
 preprocessing/ # Image normalization and augmentation tools
 utils/ # Custom metrics and visualization tools
 figures/ # Graphs and plots for documentation
 README.tex # LaTeX version of this documentation


## 3. Dataset Description

The classification model is trained and evaluated on the ODIR-5K dataset:

- 10,000 fundus images from 5,000 patients.
- Disease labels: Normal, Diabetes, Glaucoma, Cataract, AMD, Hypertension, Myopia, and Other abnormalities.

### Dataset structure for training HQ-SAM


data/
 ├── images/
 ├── segmentation_masks/
 │ ├── disc/
 │ └── cup/
 ├── labels.csv

## 4. Installation and Setup

Prerequisites

- A **Kaggle account** to access the ODIR-5K dataset.
- **Google Colab** or a GPU-enabled Python environment.
- Python 3.8+ with the following libraries:
  - torch, torchvision
  - numpy, pandas
  - scikit-learn, matplotlib
  - albumentations, opencv-python

### Installation

git clone https://github.com/your_username/ocular-disease-hqsam.git


## 5. Dataset Access via Kaggle

Visit: https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k


Download the dataset manually or via the Kaggle API.


## 6. Training Pipeline

Step 1: Fine-Tuning HQ-SAM
Input: Fundus images and ground-truth masks.
Model: HQ-SAM with frozen backbone.
Output: Refined segmentation masks for optic disc and cup.


Step 2: Biomarker Extraction
From the predicted masks:
Cup-to-disc ratio (vertical, horizontal, area-based)


Rim area, thickness


Cup eccentricity and centroid shift


Step 3: Multi-Label Classification
Classifier: ResNet50 with 8 sigmoid output nodes.


Inputs: Fundus image (optionally concatenated with biomarkers).


Loss function: Binary Cross-Entropy with class weighting.


The project includes:
Segmentation overlays (disc and cup)


Confusion matrices


Learning curves (loss and accuracy)


Examples of correct and incorrect predictions







