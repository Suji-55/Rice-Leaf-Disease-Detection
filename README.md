# Rice Leaf Disease Classification Using Deep Learning

## Project Overview
An experimental image-classification project exploring rice leaf disease recognition with transfer learning using EfficientNetB0. The notebook includes image quality checks, data augmentation, hyperparameter tuning, cross-validation, classification metrics, and Grad-CAM exploration.

> **Status:** Exploratory notebook. A leakage-free, independent test-set evaluation and end-to-end reproducibility checks are still needed. This is not a validated agricultural diagnostic tool.

## Approach
- Inspect class counts, image sizes, aspect ratios, pixel intensities, and duplicate images.
- Load labeled images from class subfolders using TensorFlow.
- Apply random horizontal flips, rotations, and zooms for augmentation.
- Build a transfer-learning classifier with ImageNet-pretrained EfficientNetB0.
- Explore Keras Tuner random search, K-fold validation, fine-tuning, classification reports, confusion matrix, per-class ROC curves, and Grad-CAM.

## Repository Contents
```text
Rice-Leaf-Disease-Detection/
├── Rice_Leaf_Disease_Pred.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Dataset
The notebook expects a local or Google Drive directory containing one subfolder per class. The dataset is **not included** in this repository. Update `dataset_path` in the configuration cell to match your own directory.

Example:
```text
data/
├── class_a/
│   └── image_001.jpg
└── class_b/
    └── image_002.jpg
```
These are illustrative folder names, not verified disease labels.

## Setup
1. Create a Python environment and install packages: `pip install -r requirements.txt`.
2. Open `Rice_Leaf_Disease_Pred.ipynb` in Google Colab or Jupyter.
3. If using Colab, mount Google Drive separately if required.
4. Update `dataset_path` in the configuration cell.
5. Run cells in order, reviewing the limitations below.

## Known Limitations / Next Steps
- Reserve a genuinely held-out test split **before** model selection, augmentation, and fine-tuning. The notebook currently evaluates on images also used in training.
- Fine-tune on training images only; do not fine-tune on the entire dataset before evaluating.
- Ensure train/validation/test splitting prevents duplicate or near-duplicate images crossing splits.
- Replace ambiguous `model` references in the Grad-CAM section with the intended trained model, and validate the Grad-CAM implementation.
- Guard against empty misclassification arrays.
- Verify model metrics after corrections before reporting any final accuracy.
- Avoid committing image datasets, tuner artifacts, credentials, or large trained weights.

## Disclaimer
For learning and portfolio demonstration only. Predictions are not a substitute for expert crop-disease diagnosis.
