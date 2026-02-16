# BreastMNIST Clinical Evaluation - Medical Imaging Classification

## Overview
This project implements a reproducible medical imaging classification pipeline using the MedMNIST BreastMNIST dataset.

The workflow includes

- Dataset exploration and distribution analysisload and explore a medical imaging dataset,
- Baseline linear modelling (Logistic Regression)
- Convolutional Neural Network implementation
- Proper train / validation / test separation
- Evaluation using ROC curves, AUC, and confusion matrices

The emphasis is on reproducibility, metric interpretation, and clinical-style evaluation rather than maximising raw accuracy.

## Project structure
- `notebooks/` — exploratory analysis, preprocessing, training, evaluation
- `src/` — reusable Python modules (preprocessing, models, evaluation)
- `results/` — exported plots and evaluation outputs
- `data/` — empty; see dataset section (no raw data committed)

## Dataset
BreastMNIST (MedMNIST benchmark)
- Grayscale 28x28 images
- Binary classification
- Public benchmark dataset
- No identifiable patient data stored in this repository

### Data governance / ethics note
- The dataset used is publicly available and provided in a preprocessed benchmark format.
- No patient-identifiable data is used or stored in this repository.
- This repository does not include any raw dataset files.
---

## Methods

### Baseline Model
Logistic Regression trained on flattened pixel intensities

### Deep Learning Model
A lightweight CNN trained with:
- Cross-entropy loss
- SGD/Adam optimisation
- Early stopping based on validation loss

Evaluation metrics:
- Accuracy
- ROC curve
- AUC
- Confusion matrix

---

## Results

### Logistic Regression
- Test Accuracy: ~0.80
- Test AUC: 0.797

![ROC - Logistic Regression](results/roc_logreg_test.png)  
![Confusion Matrix - Logistic Regression](results/cm_logreg_test.png)

### CNN Model
- Test Accuracy: 0.82  
- Test AUC: 0.862  

![ROC - CNN](results/roc_cnn_test.png)  
![Confusion Matrix - CNN](results/cm_cnn_test.png)

## Clinical Interpretation

Although accuracy improved modestly, the primary gain was in AUC, indicating improved ranking quality and reduced overlap between classes.

Improved separability allows greater flexibility in threshold selection, directly impacting false positive / false negative trade-offs. In clinical screening contexts, this is often more informative than accuracy alone.

---

## Limitations

- The dataset is small and preprocessed, limiting statistical robustness.
- Class imbalance may influence decision threshold behaviour.
- No external validation cohort was used.
- Images are low-resolution (28×28) compared to real mammography systems.
- No bias or demographic subgroup analysis was conducted.
- Mode was not evaluated within a clinical deployment environment

These factors limit direct clinical applicability and highlight the gap between benchmark performance and real-world deployment.

---

## Reproducibility

To run locally: Create and activate a virtual environment, then install dependencies:

```bash
pip install -r requirements.txt, 
```
---