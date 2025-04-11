# ☀️ SunWise Solar Potential Toolkit

This repository contains two Jupyter notebooks that together form the backend of a rooftop solar panel potential calculator. The toolkit combines image segmentation for rooftop detection with climate data extraction for solar energy forecasting.

---

## 📁 Contents

- `Rooftop_Segmentation.ipynb` — Deep learning pipeline for rooftop image segmentation using PyTorch and UNet.
- `nasa-api.ipynb` — Automated extraction of solar irradiance data from NASA's POWER API using a latitude-longitude grid.

---

## 🧠 Rooftop Segmentation Notebook

### Purpose:
Detect rooftop areas from satellite images using semantic segmentation.

### Features:
- Trains a UNet model using `segmentation-models-pytorch`
- Applies transformations to input and mask images
- Predicts rooftop regions and overlays them with an orange tint
- Saves model weights as a `.pkl` file for later use

### Sample Directory Structure:

dataset/ ├── images/ # RGB satellite images └── labels/ # Corresponding binary masks (.tif)


### Key Libraries:
- PyTorch
- torchvision
- segmentation-models-pytorch
- PIL / matplotlib

---

## 🔭 NASA API Notebook

### Purpose:
Fetch historical monthly solar irradiance data for a geographic region using NASA's POWER API.

### Features:
- Defines a bounding box of latitude-longitude values
- Queries solar radiation parameters from 2019 to 2023
- Outputs data in structured `pandas` DataFrames
- Optionally saves data to CSV for ML model training

### Data Fetched:
- `ALLSKY_SFC_SW_DWN`: All-sky surface shortwave downward radiation
- `CLRSKY_SFC_SW_DWN`: Clear-sky shortwave radiation
- `ALLSKY_SFC_SW_DNI`: Direct normal irradiance
- `ALLSKY_KT`: Clearness index
- `ALLSKY_SFC_LW_DWN`: Longwave radiation
- `CLRSKY_SFC_PAR_TOT`: Photosynthetically active radiation

### Key Libraries:
- `requests`
- `pandas`
- `numpy`
- `json`

---

## 🧪 Use Case Integration

You can use both notebooks together to:

1. Segment rooftops in satellite images.
2. Fetch solar radiation data for each rooftop's coordinates.
3. Train or use a prediction model to estimate solar panel energy yield.

---

## 💻 Tech Stack

- **ML/AI**: PyTorch, UNet, scikit-learn (optional)
- **Data**: NASA POWER API, custom rooftop imagery
- **Visualization**: matplotlib, PIL
- **Storage**: Pickle, CSV

---

## ✨ Author

Developed by **Manthan Surjuse** as part of a solar energy insight platform.

