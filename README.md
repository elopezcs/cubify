# Cubify – Warehouse Space Optimization with AI

This repository contains the research, data, and modeling pipeline for **Cubify**, an AI-driven system designed to automate parcel dimensioning and optimize warehouse storage through directed put-away.

---

## 📌 Project Overview

Cubify addresses two major warehouse inefficiencies:

- **Manual dimension measurement** (~3 minutes per box)
- **Inefficient storage placement** (random allocation → "honeycombing")

### 🚀 Proposed Solution

- **Computer Vision (CNN):** Automatically estimate box dimensions (L × W × H) in real-time
- **Optimization Engine:** Use predicted dimensions to recommend the best storage location

---

## 📂 Repository Structure

```
.
├── .venv/                                  # Local Python virtual environment
├── cubify_data_package/                    # Synthetic dataset (images + annotations)
├── outputs/
│   └── cubify_cnn_dimension_regressor/
│       ├── best_model.pt                   # Trained CNN model checkpoint
│       ├── history.csv                     # Training history (loss, metrics)
│       ├── target_stats.json               # Target normalization stats
│       ├── validation_metrics.json         # Final evaluation metrics
│       └── validation_predictions.csv      # Predictions vs ground truth
├── Cubify_CNN_Training_with_Synthetic_Data.ipynb   # CNN training notebook
├── Cubify_Synthetic_Dataset_EDA.ipynb              # Exploratory Data Analysis notebook
├── README.md
└── requirements.txt
```

---

## 📊 Notebooks

### 1. 📈 EDA Notebook
**`Cubify_Synthetic_Dataset_EDA.ipynb`**

Performs full exploratory analysis on the synthetic dataset:
- Dimension distributions (L, W, H, volume)
- Bounding box analysis
- Image statistics (brightness, sharpness)
- Correlation analysis
- Outlier detection
- Paper-ready insights

---

### 2. 🧠 CNN Training Notebook
**`Cubify_CNN_Training_with_Synthetic_Data.ipynb`**

Implements a full deep learning pipeline:
- Data loading and preprocessing
- Custom CNN model (image + bbox features)
- Training and validation loops
- Metrics:
  - MAE, RMSE, MAPE
  - R² score
  - Volume error
- Model checkpointing
- Prediction analysis

---

## 🧪 Dataset

The dataset is **synthetic**, designed to simulate real warehouse parcels.

### Includes:
- Parcel images
- Bounding boxes
- Ground-truth dimensions (cm)

### Structure:
```
cubify_data_package/
├── synthetic/
│   ├── train/
│   ├── val/
│   └── annotations/
```

---

## ⚙️ Setup

### 1. Create environment
```bash
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\activate (Windows)
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run

1. Launch Jupyter:
```bash
jupyter notebook
```

2. Run notebooks in order:
- `Cubify_Synthetic_Dataset_EDA.ipynb`
- `Cubify_CNN_Training_with_Synthetic_Data.ipynb`

---

## 📊 Outputs

After training, results are saved in:

```
outputs/cubify_cnn_dimension_regressor/
```

Key files:
- `best_model.pt` → trained model
- `validation_metrics.json` → final performance
- `validation_predictions.csv` → predictions vs actual

---

## 🎯 Project Targets

- Reduce measurement time: **3 min → <3 sec**
- Achieve dimension accuracy: **≥95%**
- Improve storage density: **+15%**

---

## 🧠 Next Steps

- Integrate real-world data (10–20%)
- Improve model architecture (ResNet / EfficientNet)
- Add depth estimation or multi-view input
- Connect to 3D bin packing optimization module

---

## 👥 Authors

- Edwin López Castañeda  
- Jarius Bedward  
- Mostafa Allahmoradi  

Conestoga College – Applied AI & Machine Learning

---

## 📜 License

This project is for academic and research purposes.
