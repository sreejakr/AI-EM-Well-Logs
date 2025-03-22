# 🛢️ AI-EM-WellLog: Resistivity Analysis in Marlim Oilfield Wells

## 📌 Project Overview

This project performs exploratory data analysis and unsupervised machine learning on synthetic resistivity well log data from the **MR3D Phase 4** dataset, modeled on the **Marlim oilfield**, a deep-water turbidite reservoir off the Brazilian coast.

The main objective is to:
- Identify **potential hydrocarbon-bearing formations**,
- Detect **geological anomalies**, and
- Flag **possible sensor issues or outliers** using data science techniques.

---

## 🧪 Dataset

**Source**: [MR3D Phase 4: Synthetic Resistivity Well Log Dataset](https://doi.org/10.3389/feart.2024.1422255)  
**Format**: `.LAS` well log files from 27 synthetic wells  
**Key Features**:
- `DEPT` – Depth (in meters)
- `RESD` – Deep resistivity (in ohm-meters)

These synthetic logs simulate real high-frequency resistivity behavior seen in petroleum reservoirs, but are clean and controlled, making them ideal for ML prototyping.

---

## 🛠️ What I Did

### 1. **Data Collection & Preprocessing**
- Parsed `.LAS` files using the `lasio` library.
- Combined all wells into one unified DataFrame.
- Cleaned null values and filtered noise.

### 2. **Domain Learning via EDA**
- As an AI Engineer without prior geophysics background, I performed:
  - **Boxplots and Histograms** to understand resistivity distributions
  - **Depth-wise scatter plots** to check for data consistency across wells
  - **High-resistivity spike analysis** to detect anomalies or geological signatures

### 3. **Outlier & Anomaly Detection**
- Identified wells with extremely high resistivity (>10,000 Ωm):
  - `1-RJS-0066`, `6-MLL-057D` (>50,000 Ωm at ~4000–4500m)
- Due to limited overlapping data at deeper depths, analysis was constrained to **depths < 4000m** for reliability.

### 4. **Depth Binning Approach**
- Used fixed depth intervals (e.g., every 100m) to:
  - Aggregate resistivity per bin
  - Analyze mean/median patterns across all wells
  - Discover stable zones vs. hydrocarbon-likely zones

### 5. **Machine Learning (Unsupervised)**
- Applied **K-Means Clustering**:
  - Grouped resistivity signals into 4 distinct formation clusters
  - Isolated high-resistivity clusters as potential hydrocarbon zones
---

## 📊 Key Observations

- **Resistivity Outliers**:
  - 3 wells (e.g., `1-RJS-0239`, `1-RJS-219A`) showed abnormal spikes between 2600–3800m.

- **Stable vs. Fluctuating Zones**:
  - 500–2000m: Stable resistivity → Homogeneous formation
  - 2500–2800m: Sharp spikes → Possible gas pockets or lithological boundaries

- **Cluster Interpretation**:
  - Low-resistivity clusters likely indicate water-filled formations.
  - High-resistivity clusters potentially signal hydrocarbon presence.

---

## 🔍 Why This Matters

Understanding subsurface resistivity variations is **critical in oil & gas exploration**. This project bridges AI with geophysics, offering:

- A **noise-free testbed** for ML models in well log interpretation
- Tools to flag potential **hydrocarbon zones**
- A hands-on approach for **AI engineers to grasp geophysical signal behavior**


## Next Steps

- Incorporate additional well logs (e.g., porosity, gamma-ray) to strengthen multi-parameter analysis.
- Apply classification models to predict formation types.
- Extend framework to real-world datasets with noise and missing data.

---
