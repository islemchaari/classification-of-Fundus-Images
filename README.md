
# High-Quality Segmentation for Improved Multi-Label Classification of Fundus Images



## 1. Overview

This project presents a deep learning framework for the automated classification of ocular diseases from retinal fundus images. The novelty lies in combining anatomical segmentation (via HQ-SAM) with ResNet-based classification enhanced by structural biomarkers.

### Main Objectives
- Segment the optic disc and cup using HQ-SAM fine-tuned for medical imaging.
- Extract clinically relevant biomarkers.
- Improve disease prediction using a ResNet50 classifier.


## 2. Repository Structure


Jupyter notebooks for preprocessing, training, evaluation
 segmentation/ # HQ-SAM fine-tuning and segmentation scripts
 classification/ # ResNet50 classifier with biomarker integration
 preprocessing/ # Image normalization and augmentation tools
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



## 5. Dataset Access via Kaggle

Visit: https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k


Download the dataset manually or via the Kaggle API.


## 6. Training Pipeline

This section describes the full pipeline, from segmentation to classification, that you can run end-to-end.

---

### Step 1 — Fine-Tuning HQ-SAM (Segmentation)

- **Input:** Fundus images and ground-truth masks  
- **Model:** HQ-SAM with frozen backbone  
- **Output:** Refined segmentation masks for the optic disc and cup  

**Additional resources (segmentation model + training dataset + ground-truth masks):**  
👉 [Google Drive folder](https://drive.google.com/drive/folders/1EKgiTBl2HqMkhrgnPAs0IXaD-1f-Fqda)

---

### Step 2 — Biomarker Extraction

From the predicted masks, we compute structural biomarkers:

- Cup-to-disc ratio (vertical, horizontal, area-based)  
- Neuro-retinal rim area and thickness  
- Cup eccentricity  
- Centroid shift (distance between cup and disc centers)  

---

### Step 3 — Multi-Label Classification

- **Classifier:** ResNet50 with 8 sigmoid output nodes  
- **Inputs:** Fundus image (optionally concatenated with biomarkers)  
- **Loss function:** Binary Cross-Entropy with class weighting  

---

### Project Outputs

The pipeline produces the following results and visualizations:

- Segmentation overlays (disc and cup boundaries)  
- Confusion matrices for classification performance  
- Learning curves (training/validation loss and accuracy)  
- Examples of predictions  

---

With this workflow, segmentation and biomarker extraction enhance disease classification, especially for structure-dependent conditions such as glaucoma.











