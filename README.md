# Ultrasound Breast Cancer Image Classification

![Project Banner](path_to_your_banner_image.png)

This repository contains a deep learning project for **classifying breast cancer from ultrasound images**. The model is designed to accurately distinguish between **benign** and **malignant** cases using state-of-the-art convolutional neural networks.

---

# Ultrasound Breast Cancer Classification Using Deep Learning

## Table of Contents
1. Project Overview
2. Related Work
3. Dataset
4. Methodology
   - Data Preprocessing
   - Model Architectures
   - Training Strategy
5. Evaluation Metrics
6. Results and Discussion
7. Repository Structure
8. How to Run the Project
9. Poster and Slides
10. Limitations and Future Work
11. References
12. Acknowledgements

---

## 1. Project Overview

Breast cancer is one of the most common life-threatening diseases among women worldwide. Early diagnosis significantly improves treatment outcomes. Ultrasound imaging is a non-invasive and cost-effective modality and is especially suitable for dense breast tissue.

This project implements an automated deep learning–based system to classify breast ultrasound images into three categories: normal, benign, and malignant. Multiple convolutional neural network architectures and transfer learning approaches are explored and compared to analyze performance, robustness, and clinical relevance.

---

## 2. Related Work

Recent research in medical image analysis has demonstrated the effectiveness of convolutional neural networks for ultrasound image classification. Transfer learning using ImageNet-pretrained models such as ResNet and AlexNet is commonly applied to overcome limited dataset size and improve feature representation.

The Breast Ultrasound Images Dataset (BUSI) has been widely used in prior studies for automated breast lesion classification and provides both image-level labels and lesion masks.

---

## 3. Dataset

The project uses the Breast Ultrasound Images Dataset (BUSI), which consists of ultrasound images grouped into three classes:
- Normal
- Benign
- Malignant

For benign and malignant cases, corresponding ground-truth lesion masks are available. These masks are used in one experimental setup to generate overlay images that emphasize lesion regions.

---

## 4. Methodology

### Data Preprocessing

Data preprocessing is handled through scripts located in the `tools/` directory.

The preprocessing pipeline includes:
- Automated dataset download
- Image resizing to 224 × 224
- RGB conversion
- Label extraction from directory structure
- Generation of an overlay dataset using lesion masks:
  - Background regions are darkened for benign and malignant images
  - Normal images remain unchanged

![Data Preprocessing Pipeline](assets/preprocessing_pipeline.png)

---

### Model Architectures

Five model configurations were implemented and evaluated:

1. Custom CNN trained from scratch using original images  
2. ResNet50 with transfer learning (ImageNet pretrained)  
3. Custom CNN trained on mask-overlay images with hyperparameter optimization  
4. Custom CNN baseline variant with reduced training schedule  
5. AlexNet with transfer learning (ImageNet pretrained)

![Custom CNN Architecture](assets/custom_cnn_architecture.png)
![Transfer Learning Architecture](assets/transfer_learning_architecture.png)

---

### Training Strategy

All models are trained using supervised learning with cross-entropy loss.

Training configuration includes:
- Optimizers: SGD and AdamW
- Learning rate scheduling with cosine annealing and warm-up
- Variable batch sizes depending on experiment
- GPU acceleration when available

To address class imbalance, weighted loss functions and weighted sampling are applied, with a focus on improving malignant class sensitivity.

![Training Workflow](assets/training_workflow.png)

---

## 5. Evaluation Metrics

Model performance is evaluated using the following metrics:
- Accuracy
- Precision
- Recall (Sensitivity)
- F1-Score
- F2-Score (recall-oriented)
- Balanced Accuracy
- ROC-AUC for malignant class
- Confusion Matrix

Malignant detection is additionally treated as a binary classification task to reflect clinical screening priorities.

---

## 6. Results and Discussion

All models are evaluated on a held-out test set using consistent evaluation metrics.

Visual results include:
- Training and validation loss curves
- Training and validation accuracy curves
- Confusion matrices
- ROC curves for malignant detection

![Loss Curve](Loss Curve.png)
![Accuracy Curve](Accuracy Curve.png)

Additional result visualizations are available in:
- `notebooks/final plots of results.ipynb`

---

## 7. Repository Structure


## Dataset

The dataset used in this project is the **[Dataset Name]**, containing **N images** of ultrasound breast scans.

| Class      | Number of Images | Percentage |
|------------|----------------|-----------|
| Benign     | XXX            | XX%       |
| Malignant  | XXX            | XX%       |
| Total      | XXX            | 100%      |

**Dataset Source:** [Provide URL or reference]

**Folder Structure Example:**
