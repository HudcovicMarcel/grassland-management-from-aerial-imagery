
<h1 align="center">
  <br>
  <img src="assets/logo.png" width="300" alt="GMAI Logo">
  <br>
  Grassland Management from Aerial Imagery (GMAI)
  <br>
</h1>

<p align="center">

  <!-- Google Colab badge -->
  <a href="https://colab.research.google.com/YOUR_NOTEBOOK_LINK">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab">
  </a>

  <!-- Zenodo DOI badge -->
  <a href="https://doi.org/YOUR_DOI_HERE">
    <img src="https://zenodo.org/badge/DOI/YOUR_DOI_HERE.svg" alt="DOI">
  </a>

  <a href="https://your-project-website.com">
  <img src="https://img.shields.io/badge/Grasslands4Biodiversity-Website-green" alt="Grasslands4Biodiversity">
</a>

</p>


## Description

This repository serves as **supplementary material** and **release** of the code and dataset for the paper:

*Country-wide object detection of grassland management practices from aerial imagery using deep learning, case study: Slovak Republic* **(in preparation)**.

Our study trains the **YOLO11** model (Jocher & Qiu, 2024) to detect objects representing grassland management practices in aerial imagery from the third cycle of the orthophotomosaic of the **Slovak Republic** (2023), with a ground sampling distance of **15 cm**.

## Dataset content

This dataset consist 1147 manually labeled images (1280x1280px) that were further augmented, and split into Train (~60%), Test (~20%), and Validation (~20%) sets.

**Count of labels for each class:**
| Class           | Type       | Train | Test | Val  |
|-----------------|------------|-------|------|------|
| Cattle          | Original   | 4875  | 1935 | 1737 |
|                 | Augmented  | 5646  | 1602 | 1683 |
| Sheep           | Original   | 4242  | 1184 | 2224 |
|                 | Augmented  | 5733  | 1604 | 1621 |
| Horse           | Original   | 759   | 241  | 227  |
|                 | Augmented  | 4944  | 1730 | 1915 |
| Round Haybale   | Original   | 3522  | 1183 | 877  |
|                 | Augmented  | 4027  | 1189 | 1134 |
| Square Haybale  | Original   | 461   | 209  | 309  |
|                 | Augmented  | 3860  | 1568 | 1425 |
| Haystack        | Original   | 163   | 30   | 31   |
|                 | Augmented  | 945   | 282  | 341  |
| Machinery       | Original   | 75    | 15   | 19   |
|                 | Augmented  | 448   | 161  | 154  |

> **Note:**  
> - The applied augmentation techniques are described in the paper.  
> - **Original** - labels on non-augmented images.  
> - **Augmented** - labels on augmented images.

## Data

Hosted on **Zenodo**:

```bash

10.5281/zenodo.17350381/
│
├── dataset.zip/               # Augmented and split images used for YOLO11 training and validation
│   ├── train/                 # Training subset ≈ 60%
│   │   ├── images/ 
│   │   └── val/ 
│   ├── test/                  # Test subset ≈ 20%
│   │   ├── train/
│   │   └── val/ 
│   ├── val/                   # Val subset ≈ 20%
│   │   ├── train/
│   │   └── val/ 
│   └── dataset.yaml           # YAML file for training setup
│
│
├── results.zip/               # Jupyter notebooks
    └── EDA.ipynb              # Exploratory Data Analysis example

```

Hosted on **GitHub**:

```bash
grassland-management-from-aerial-imagery/
│
├── readme.md                  # Project overview and instructions
├── LICENSE                    # License file
├── requirements.txt           # Python dependencies
│
├── assets/                    # Images, logos, and visual assets
│   └── img/
│       └── logo.png
│
├── data/                      # Datasets (raw and processed)
│   ├── raw/                   # Original unprocessed data (e.g., aerial images)
│   ├── processed/             # Preprocessed images for training/testing
│   └── annotations/           # YOLO annotations or other labels
│
├── notebooks/                 # Jupyter notebooks
│   └── EDA.ipynb              # Exploratory Data Analysis example
│
├── src/                       # Source code
│   ├── models/                # Model architectures or scripts
│   ├── utils/                 # Helper functions (preprocessing, metrics)
│   └── train.py               # Training script
│
├── results/                   # Model outputs
│   ├── predictions/           # Example inference results
│   └── metrics/               # Evaluation metrics, plots
│
├── colab/                     # Google Colab notebooks (optional)
│   └── GMAI_demo.ipynb
│
└── docs/                      # Documentation or supplementary info
    └── paper/                 # Supplementary material for the pape
```



## Usage

Full workflow is in notebook.

## Results

Results of our study are hosted on Zenodo.

**Predictions Across Slovak Orthophotomosaic Cycles**

| Class           | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|-----------------|------|------|------|------|------|------|------|
| **Cattle**       | 7,203  | 23,470 | 33,507 | 6,402  | 37,262 | 31,872 | 9,384 |
| **Sheep**        | 5,074  | 77,426 | 97,192 | 8,143  | 83,338 | 60,419 | 5,486 |
| **Horse**        | 1,028  | 1,502  | 468    | 894    | 1,454  | 1,367  | 1,747 |
| **Round Haybale**| 2,764  | 30,634 | 40,014 | 7,465  | 56,751 | 27,802 | 5,760 |
| **Square Haybale**| 148   | 362    | 971    | 84     | 820    | 174    | 12    |
| **Haystack**     | 116    | 360    | 176    | 72     | 769    | 38     | 284   |
| **Machinery**    | 206    | 401    | 455    | 249    | 596    | 278    | 242   |

## Credits

- Aerial imagery is under **CC BY Creative Commons Attribution (GKÚ Bratislava, NLC) 4.0**.  
- **YOLO11** model by **Ultralytics** (Jocher & Qiu, 2024).  
  Citation: Jocher, G. & Qiu, J. (2024). *Ultralytics YOLO11*, version 11.0.0. Available at: [https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics). License: AGPL-3.0.
- README template adapted from **[Electron Markdownify](https://github.com/amitmerchant1990/electron-markdownify)** by Amit Merchant.


## License

MIT



