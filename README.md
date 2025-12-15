# Rivers and Rotation: Characteristics of Tornado Pathlength and Width near the Upper Mississippi River, 1950-2024

**Author:** Nathan Makowski  
**Course:** ATMS 596 – Capstone Project  
**Language:** Python (Jupyter Notebooks)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Geospatial](https://img.shields.io/badge/Geospatial-GeoPandas%20%7C%20Shapely-green)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Project Overview

This repository contains the complete analysis workflow for a capstone research project examining whether tornado characteristics (path length and width) change when tornadoes cross or occur near the Mississippi River.  

Using **GIS-based spatial analysis**, long-term **SPC tornado records (1950–2024)**, and **high-resolution Mississippi River shapefiles**, this study evaluates whether large rivers act as modifying land–surface features for tornado intensity or persistence.

The primary focus is on:
- Tornado **path length** (persistence proxy)
- Tornado **path width** (instantaneous intensity proxy)
- Comparisons between tornadoes that **cross**, **approach**, or **remain distant from** the Mississippi River

---

## 📂 Repository Contents

This repository is organized around a set of Jupyter Notebooks, each corresponding to a specific analysis subset or intensity group.

### 🧪 Jupyter Notebooks

| Notebook | Description |
|--------|-------------|
| `Results_6_EF_0-1.ipynb` | Analysis of **weak tornadoes (EF0–EF1)** near and crossing the Mississippi River. Includes spatial classification, statistical testing, and visualization. |
| `Results_8_EF_0-1.ipynb` | Expanded **EF0–EF1 analysis** with additional diagnostics, mapping, and validation checks. |
| `Results_9_EF_0-5.ipynb` | **All tornadoes (EF0–EF5)** combined. Serves as the primary full-sample analysis notebook. |
| `Results_10_EF_2-5.ipynb` | Analysis restricted to **strong tornadoes (EF2–EF5)** to test river effects on higher-intensity events. |
| `Results_11_EF_0-5.ipynb` | Final synthesis notebook including robustness checks, subsampling, and summary statistics. |

Each notebook is fully documented and can be run independently once the data paths are configured.

---

## 🗂️ Data Sources

### 🌪️ Tornado Data
- **Source:** NOAA Storm Prediction Center (SPC)  
- **Dataset:** “Actual_Tornadoes”  
- **Period:** 1950–2024  
- **Access:**  
  https://www.spc.noaa.gov/wcm/#data

This dataset includes start/end latitude and longitude coordinates, pre-F/F/EF-scale ratings, path length, and width.

---

### 🌊 Mississippi River Geometry
- **Source:** Upper Midwest Environmental Sciences Center (UMESC)  
- **Dataset:** Land–Water Classification Polygons  
- **Access:**  
  https://www.umesc.usgs.gov/data_library/geospatial_data/land_water_classification.html

These shapefiles are used to construct a high-resolution Mississippi River polygon and derive a 10 km buffer zone for spatial classification.

---

## 🧠 Methodology Summary

- Tornado tracks reconstructed from SPC start/end coordinates
- River geometry derived from UMESC water polygons
- Spatial classification into:
  - West of river
  - East of river
  - Crossing / within 10 km of river
- Statistical testing using:
  - Kruskal–Wallis tests
  - Pairwise post-hoc comparisons
- Subsampling applied to address sample-size imbalance

All spatial analyses are performed in **UTM Zone 15N** to ensure accurate distance calculations.

---

## ⚙️ Requirements

Key Python packages:
- `pandas`
- `numpy`
- `geopandas`
- `shapely`
- `matplotlib`
- `seaborn`
- `scipy`
- `cartopy`
- `plotly`

Recommended environment:  
```bash
conda create -n xarray-climate python=3.11
conda activate xarray-climate