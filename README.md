# Rivers and Rotation: Characteristics of Tornado Pathlength and Width near the Upper Mississippi River, 1950-2024

**Author:** Nathan Makowski  
**Course:** ATMS 596 – Capstone Project  
**Language:** Python (Jupyter Notebooks)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Geospatial](https://img.shields.io/badge/Geospatial-GeoPandas%20%7C%20Shapely-green)
![Cartopy](https://img.shields.io/badge/Cartopy-Mapping-lightgrey)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📌 Project Overview

This repository contains the complete geospatial and statistical workflow for a capstone research project examining whether tornado characteristics systematically change near or across the Upper Mississippi River.

Using:
- NOAA Storm Prediction Center tornado records (1950–2024)
- High-resolution Mississippi River polygon geometries
- GIS-based spatial analysis
- Nonparametric statistical testing
- Monte Carlo and resampling methodologies

this project evaluates whether large river systems influence tornado:
- **path length** (storm persistence proxy)
- **path width** (instantaneous intensity proxy)
- spatial evolution
- nocturnal behavior
- outbreak-related characteristics

The study focuses primarily on tornadoes occurring within a 10 km buffer surrounding the Upper Mississippi River and compares them against geographically separated control populations east and west of the river.

---

## 🎯 Research Questions

This project investigates several core questions:

1. Do tornadoes weaken, strengthen, narrow, or widen near large river systems?
2. Are tornado path lengths altered when crossing the Mississippi River?
3. Do nocturnal tornadoes behave differently near the river corridor?
4. Are observed differences robust to:
   - EF-scale distributions
   - sample-size imbalance
   - outbreak clustering
   - control population selection?
5. Are river-adjacent tornado characteristics distinguishable from broader regional climatology?

---

## 📂 Repository Contents

This repository is organized around a set of Jupyter Notebooks, each corresponding to a specific analysis subset or intensity group.

### 🧪 Jupyter Notebooks

#### 🌪️ Data Preparation & Spatial Classification

| Notebook | Description |
|---|---|
| `SPC_Storm_Reports_Script.ipynb` | Processes SPC tornado records, reconstructs tornado tracks from start/end coordinates, and prepares geospatial tornado datasets for analysis. |
| `Crossed_River_West_East_Control.ipynb` | Constructs the primary river-crossing, west-control, and east-control tornado populations using Mississippi River geometries and spatial filtering. |
| `West_Side_East_Side_Crossed_River.ipynb` | Refines spatial classifications and develops side-based tornado groupings for statistical comparison and visualization. |

---

#### 📊 EF-Scale and Core Statistical Analyses

| Notebook | Description |
|---|---|
| `Results_6_EF_0-1.ipynb` | Initial weak tornado (EF0–EF1) analysis comparing tornado path length and width near/crossing the river. |
| `Results_8_EF_0-1.ipynb` | Expanded EF0–EF1 analysis with additional diagnostics, visualization, and robustness checks. |
| `Results_9_EF_0-5.ipynb` | Full-sample analysis including all tornadoes (EF0–EF5); serves as a primary baseline notebook. |
| `Results_10_EF_2-5.ipynb` | Analysis restricted to stronger tornadoes (EF2–EF5) to investigate river effects on more intense events. |
| `Results_11_EF_0-5.ipynb` | Expanded all-tornado analysis including revised statistical comparisons and additional spatial diagnostics. |
| `Results_12_Storm_Reports_Added.ipynb` | Incorporates SPC storm report information and supplemental tornado-event metadata into the analysis workflow. |
| `Results_13_EF_0-5.ipynb` | Advanced statistical comparisons and revised visualization suite for full-population tornado analyses. |
| `Results_14_EF_0-5.ipynb` | Additional robustness testing including revised sampling strategies and expanded pairwise comparisons. |
| `Results_15_Median_Path_Length_Calculations.ipynb` | Computes median path length diagnostics and supporting statistical summaries used throughout the project. |
| `Results_16_EF_0-5.ipynb` | Monte Carlo and resampling-based validation experiments for tornado path length and width comparisons. |
| `Results_17_EF_0-5.ipynb` | Final synthesis notebook integrating robustness analyses, resampled controls, and refined statistical outputs. |

---

#### 🌙 Diurnal & Nocturnal Analyses

| Notebook | Description |
|---|---|
| `Results_Diurnal_Nocturnal.ipynb` | Separates tornadoes into diurnal and nocturnal populations for comparative river-adjacent analysis. |
| `Results_Diurnal_Nocturnal_2.ipynb` | Expanded temporal classification analysis with revised sampling and additional visualization diagnostics. |
| `Results_Nocturnal_Literature.ipynb` | Literature-guided nocturnal tornado classification and comparison framework. |
| `Results_Nocturnal_Symmetric.ipynb` | Symmetric nocturnal subdivision analysis using transition periods, core nighttime periods, and river-relative classifications. |

---

#### 🌩️ Outbreak Analyses

| Notebook | Description |
|---|---|
| `Results_Outbreak.ipynb` | Identifies outbreak and non-outbreak tornado populations using clustering approaches and temporal grouping methodologies. |
| `Results_Outbreak_2.ipynb` | Expanded outbreak analysis including DBSCAN clustering sensitivity tests, temporal windows, and outbreak robustness diagnostics. |

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
  https://www.umesc.usgs.gov/data_library/aqa_feat_bath_str/land_water.html

These shapefiles are used to construct a high-resolution Mississippi River polygon and derive a 10 km buffer zone for spatial classification.

---

## 🧠 Methodology Summary

### 1️⃣ Tornado Track Reconstruction

SPC tornado start and end coordinates were converted into geospatial line segments using:
- `GeoPandas`
- `Shapely`

All tornadoes were projected into:
- **UTM Zone 15N**

to ensure accurate distance and area calculations.

---

### 2️⃣ Mississippi River Processing

River polygons were:
- merged into continuous geometries
- spatially clipped to the Upper Mississippi River study region
- buffered outward by 10 km

This produced:
- river-crossing tornado classifications
- river-adjacent tornado populations
- east/west control regions

---

### 3️⃣ Spatial Classification

Tornadoes were categorized into:
- Crossed River
- West Side
- East Side
- West Control
- East Control
- Buffer/River populations

Additional classifications included:
- Diurnal
- Nocturnal
- Symmetric nocturnal bins
- Outbreak vs non-outbreak events

---

### 4️⃣ Statistical Analysis

Primary statistical methods included:
- Kruskal–Wallis tests
- Pairwise post-hoc comparisons
- Bonferroni-adjusted significance testing
- Monte Carlo resampling
- Bootstrap-style intensity matching
- Median comparison diagnostics

Variables analyzed:
- Tornado path length
- Tornado width
- EF-scale distributions
- Diurnal/nocturnal characteristics

---

### 5️⃣ Intensity-Matched Resampling

To address unequal sample sizes and EF-scale biases:
- Control populations were conditionally resampled
- EF-scale distributions were matched between comparison groups
- 10,000-iteration Monte Carlo experiments were conducted for robustness testing

These procedures helped determine whether apparent river effects persisted after accounting for climatological intensity differences.

---

### 6️⃣ Outbreak Classification

Additional analyses investigated whether outbreak clustering influenced results.

Methods included:
- DBSCAN clustering
- Sequential temporal clustering
- Variable temporal windows:
  - 6-hour
  - 12-hour
  - 24-hour
- Variable spatial thresholds

Outbreak and non-outbreak tornadoes were then analyzed separately.

---

## 📈 Key Analysis Themes

The notebooks collectively evaluate:
- River-crossing tornado persistence
- Tornado width variability near rivers
- Diurnal versus nocturnal tornado behavior
- Outbreak-related biases
- Spatial asymmetries east and west of the Mississippi River
- Sensitivity to sample balancing and control selection

---

## 🗺️ Visualization & Mapping

The project includes:
- GIS-based tornado track maps
- Mississippi River overlay visualizations
- Boxplots
- Violin plots
- Histograms
- Density plots
- Monte Carlo distribution plots
- Temporal classification figures

Mapping libraries include:
- `Cartopy`
- `GeoPandas`
- `Matplotlib`

---

## ⚙️ Requirements

### Core Python Packages

```bash
pandas
numpy
geopandas
shapely
matplotlib
seaborn
scipy
cartopy
plotly
scikit-learn
pyproj
```

---

## 🐍 Recommended Environment

```bash
conda create -n xarray-climate python=3.11
conda activate xarray-climate

pip install pandas numpy geopandas shapely matplotlib seaborn scipy \
cartopy plotly scikit-learn pyproj
```

---

## ▶️ Running the Notebooks

1. Download SPC tornado datasets
2. Download UMESC river shapefiles
3. Update local file paths within notebooks
4. Launch Jupyter Notebook or JupyterLab
5. Run notebooks sequentially or independently

Example:

```bash
jupyter lab
```

---

## ⚠️ Notes

- Several notebooks represent iterative development and robustness testing.
- Some analyses intentionally overlap to validate consistency across methodological changes.
- Statistical significance may vary depending on:
  - EF-scale filtering
  - resampling strategy
  - outbreak classification
  - nocturnal subdivision
  - control population selection

---

## 📚 Future Work

Potential extensions include:
- Environmental reanalysis integration
- Terrain and land-use interactions
- Radar-derived tornado intensity estimates
- Expanded river systems beyond the Mississippi River
- Machine learning classification approaches
- Tornado lifecycle segmentation near river crossings

---

## 📄 License

This project is licensed under the MIT License (see above).

---

## 🙏 Acknowledgments

- NOAA Storm Prediction Center (SPC)
- Upper Midwest Environmental Sciences Center (UMESC)
- University of Illinois Urbana-Champaign
- Online M.S. Program in Weather and Climate Risk & Data Analytics 
