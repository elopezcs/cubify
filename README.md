# Cubify Synthetic Dataset EDA

Exploratory data analysis for the **Cubify** synthetic parcel dataset used in the computer-vision dimensioning track of the warehouse space optimization project.

This repository is centered on a Jupyter notebook that analyzes a synthetic-only dataset designed for early-stage research on:

- automated parcel dimension estimation from images
- conveyor-friendly warehouse vision pipelines
- downstream support for directed put-away and storage optimization

The notebook is intended to support the **dataset**, **methods**, **EDA**, **limitations**, and **experimental setup** sections of the Cubify research paper.

---

## Project context

Cubify is motivated by a warehouse process in which parcel measurement is slow and manual, and storage placement often depends on operator judgment rather than data-driven optimization. The broader project goal is to support faster parcel measurement, higher-throughput inbound handling, and better storage density through AI-based dimensioning and optimization.

This notebook focuses on only one part of that pipeline:

**synthetic dataset exploratory data analysis for the vision module**

It does **not** train a model. Instead, it evaluates the dataset quality and structure so the team can justify later modeling decisions.

---

## What this notebook covers

The notebook performs a full EDA on the synthetic dataset package and answers questions such as:

1. What is in the dataset?
2. Are the train and validation splits balanced and comparable?
3. How are parcel dimensions distributed?
4. How diverse are parcel shapes and projected 2D footprints?
5. Are the annotations internally consistent?
6. Are there image-level quality issues that may affect learning?
7. What findings are useful for the Cubify paper?
8. What limitations should be stated clearly before model training?

The notebook includes both **Markdown discussion** and **code cells** so that it can function as a research artifact, not just a script.

---

## Repository contents

A typical repository structure should look like this:

```text
.
├── Cubify_Synthetic_Dataset_EDA.ipynb
└── cubify_data_package/
    └── synthetic/
        ├── train/
        │   └── images/
        ├── val/
        │   └── images/
        └── annotations/
            ├── train_coco.json
            ├── train_metadata.csv
            ├── val_coco.json
            └── val_metadata.csv
```

If you prefer, you can keep the dataset as a ZIP outside the repo and extract it locally before running the notebook.

---

## Dataset summary

The EDA notebook analyzes a synthetic parcel dataset with:

- **1,500 synthetic images total**
- **1,250 training images**
- **250 validation images**
- **COCO-style annotations**
- **CSV metadata** containing physical parcel dimensions and projected 2D bounding-box information

Each metadata row includes fields such as:

- `image_id`
- `file_name`
- `length_cm`
- `width_cm`
- `height_cm`
- `bbox_x`
- `bbox_y`
- `bbox_w`
- `bbox_h`
- `belt_y`
- `side_sign`

This makes the dataset suitable for early experiments in:

- direct dimension regression
- multi-target prediction
- annotation verification
- synthetic-data quality analysis

---

## Main sections inside the notebook

The notebook is organized into these sections:

1. **Load metadata and annotations**
2. **Dataset overview**
3. **Annotation integrity checks**
4. **Summary statistics for regression targets**
5. **Parcel shape diversity**
6. **Projected 2D footprint and annotation geometry**
7. **Correlation structure**
8. **Image-level quality proxies**
9. **Visual audit of sample images**
10. **Train/validation split comparability**
11. **Outliers and edge cases**
12. **Paper-ready findings and implications**
13. **Recommended next analytical steps**

---

## Key outcomes from the EDA

The notebook produces several practical insights that are useful for the research paper and for future model design:

- the dataset package is internally clean and consistent
- parcel dimensions span a broad range rather than a narrow size regime
- projected 2D footprints are diverse, which is helpful for robustness
- image geometry shows meaningful relationships with physical parcel targets
- train and validation distributions are sufficiently similar for early proof-of-concept experiments
- synthetic-only analysis is useful for early development, but it does **not** prove sim-to-real performance

In other words, this notebook supports the argument that the dataset is suitable for **initial model development and controlled experimentation**, while also documenting why real-world fine-tuning and validation will still be necessary later.

---

## Requirements

The notebook uses a lightweight Python stack:

```text
python >= 3.10
numpy
pandas
matplotlib
Pillow
jupyter
notebook
```

You can install the core dependencies with:

```bash
pip install numpy pandas matplotlib pillow jupyter notebook
```

---

## How to run

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <your-repo-folder>
```

### 2. Ensure the dataset folder is available

Place the extracted dataset in the repository so that the notebook can find:

```text
cubify_data_package/synthetic/
```

### 3. Launch Jupyter

```bash
jupyter notebook
```

Then open:

```text
Cubify_Synthetic_Dataset_EDA.ipynb
```

### 4. Run all cells

The notebook is designed to be readable from top to bottom. Running all cells will:

- load metadata and annotations
- compute summary statistics
- generate visualizations
- compare train and validation splits
- surface outliers and risks
- produce paper-ready analytical takeaways

---

## Outputs generated by the notebook

Running the notebook produces:

- summary tables
- statistical descriptions of dimensions and volumes
- shape and footprint analysis
- correlation visualizations
- image-level quality checks
- sample-image visual audits
- outlier analysis
- a reusable narrative section for the Cubify paper

Because outputs are embedded in the notebook, the repository can also be used as a **static research artifact** for review by team members, instructors, or collaborators.

---

## Suggested use in the Cubify paper

This notebook is especially useful when writing:

- the **dataset description** section
- the **EDA / preprocessing** section
- the **methodology justification** section
- the **limitations** section
- the **future work** section

A practical way to use it is:

1. run the notebook after any dataset change
2. capture updated figures and tables
3. reuse the paper-ready findings section as the basis for written discussion
4. reference the notebook in the repository as the reproducible EDA artifact

---

## Limitations

This notebook analyzes a **synthetic-only** dataset.

That means:

- it can validate internal dataset consistency
- it can justify early model development choices
- it can help design experiments
- but it cannot establish real-world generalization on its own

Real conveyor imagery, real lighting conditions, real carton defects, motion blur, reflective surfaces, and operational occlusions still need to be introduced in later stages of the project.

---

## Recommended next steps

After this EDA, the natural next steps are:

1. baseline dimension-regression experiments on the synthetic dataset
2. augmentation studies for blur, brightness, and scale changes
3. error analysis by parcel size regime
4. ablation experiments for alternative prediction heads
5. synthetic-to-real transfer once real parcel data is available

---

## Reproducibility notes

To keep results reproducible:

- keep the dataset folder structure unchanged
- avoid renaming annotation files unless notebook paths are also updated
- commit the notebook with outputs when you want GitHub readers to view charts without rerunning it
- clear outputs only when you need a lighter repository history

---

