
<h1 align="center">
  <br>
  <img src="assets/logo.png" width="300" alt="GMAI Logo">
  <br>
  Grassland Management from Aerial Imagery (GMAI)
  <br>
</h1>

<p align="center">

  <a href="https://colab.research.google.com/drive/1jJHC4HpZEuSOq6CaCesBxK_DqZXVWK0z?usp=sharing">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab">
  </a>
  
  <a href="https://doi.org/10.5281/zenodo.17350381">
    <img src="https://zenodo.org/badge/DOI/10.5281/zenodo.17350381.svg" alt="DOI"></a>
  </a>

  <a href="https://www.grass4b.com/_sub/">
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
│   │   └── labels/ 
│   ├── test/                  # Test subset ≈ 20%
│   │   ├── images/
│   │   └── labels/ 
│   ├── val/                   # Val subset ≈ 20%
│   │   ├── images/
│   │   └── labels/ 
│   └── dataset.yaml           # Configuration file specifying dataset paths, class names, and train/val/test splits for YOLO training
│      
├── YOLO11x_GMAI.pt            # PyTorch checkpoint of the YOLO11x model trained on the GMAI dataset
│
├── GMAI_OD_results.gpkg       # Results across the three Slovak orthophoto cycles (2017–2023)
│
└── demo_data.zip              # Contains exemplary data for running the workflow in the Google Colab notebook (for demonstration and replication)
```
> **Note:**  
> In *dataset.zip*, all files whose names end with a non-numeric character correspond to augmented data instances, while numeric suffixes indicate original samples.

## Usage

A full end-to-end workflow is available in the accompanying Google Colab notebook. It provides step-by-step code, methodological explanations, and the ability to replicate the workflow using included demo data.

## Results

Results of our study are provided as a GeoPackage file hosted on Zenodo.  
Each polygon in the dataset contains a set of attributes describing:

- **Predicted class** (class_id/class_name : 0/Cattle, 1/Haybale round, 2/Square haybale, 3/Haystack, 4/Horse, 5/Machinery, 6/Sheep)
- **Type of management practice** (mowing/grazing)
- **Prediction confidence** of the YOLO11x model (confidence)
- **Acquisition date** of the orthophoto from which the object was detected (Datum)

All geometries are stored in the **S-JTSK / Krovak East North (EPSG:5514)** coordinate reference system.

<img src="assets/example.png" width="2000" alt="Example">

**Predictions Across Slovak Orthophotomosaic Cycles**

| Class           | 2017   | 2018   | 2019   | 2020  | 2021   | 2022   | 2023  |
|-----------------|--------|--------|--------|-------|--------|--------|-------|
| **Cattle**       | 7,203  | 23,470 | 33,507 | 6,402 | 37,262 | 31,872 | 10,056 |
| **Sheep**        | 5,074  | 77,426 | 97,192 | 8,143 | 83,338 | 60,419 | 6,277  |
| **Horse**        | 1,028  | 1,502  | 468    | 894   | 1,454  | 1,367  | 1,767  |
| **Round Haybale**| 2,764  | 30,634 | 40,014 | 7,465 | 56,751 | 27,802 | 6,738  |
| **Square Haybale**| 148   | 362    | 971    | 84    | 820    | 174    | 80     |
| **Haystack**     | 116    | 360    | 176    | 72    | 769    | 38     | 301    |
| **Machinery**    | 206    | 401    | 455    | 249   | 596    | 278    | 253    |

## Credits

- Aerial imagery is under **CC BY Creative Commons Attribution (GKÚ Bratislava, NLC) 4.0**.  
- **YOLO11** model by **Ultralytics** (Jocher & Qiu, 2024).  
  Citation: Jocher, G. & Qiu, J. (2024). *Ultralytics YOLO11*, version 11.0.0. Available at: [https://github.com/ultralytics/ultralytics](https://github.com/ultralytics/ultralytics). License: AGPL-3.0.
- README template adapted from **[Electron Markdownify](https://github.com/amitmerchant1990/electron-markdownify)** by Amit Merchant.


## License

**Creative Commons Attribution 4.0 International (CC BY 4.0)**

You are free to share, adapt, and build upon the materials for any purpose, provided appropriate credit is given.

If you use the GMAI dataset, please cite:
Hudcovič, M. (2025). Grassland Management from Aerial Imagery (GMAI) [Data set]. Zenodo. https://doi.org/10.5281/zenodo.17350381


