# HABs Prediction - Sarasota Bay

Forecasting harmful algal blooms in Sarasota Bay using machine learning and environmental data.

## Overview

This project develops machine learning models to predict daily red tide (Karenia brevis) occurrence in Sarasota Bay, Florida. The system integrates historical monitoring records with satellite-derived environmental data to provide early warning capability for coastal management.

## Key Features

- **Multiple ML Architectures**: Logistic Regression, Random Forest, XGBoost, LSTM
- **Multimodal Data Integration**: FWC monitoring + NASA MODIS + NOAA CoastWatch
- **High Accuracy**: 91.8% accuracy, 96.8% recall (Random Forest)
- **Daily Predictions**: Operational forecasting at daily temporal resolution
- **Feature Importance Analysis**: Identifies key environmental drivers

## Results

- Random Forest: 91.8% accuracy, 94.2% AUC, 96.8% recall
- XGBoost: 91.8% accuracy, 97.2% recall (fewest missed blooms)
- Lag features (7-day, 14-day bloom history) account for 80% of predictive power
- Environmental variables (SST, chlorophyll, light attenuation) contribute <5%

## Data Sources

- **FWC HAB Monitoring**: Historical Karenia brevis cell counts (2015-2023)
- **NASA MODIS Aqua**: Chlorophyll-a, light attenuation (8-day composites)
- **NOAA CoastWatch**: Sea surface temperature (daily, 5km resolution)


## Installation
```bash
git clone https://github.com/yourusername/habs-prediction-sarasota.git
cd habs-prediction-sarasota
pip install -r requirements.txt
```

## Usage
```python
# Train Random Forest model
python src/train_model.py --model random_forest --data data/processed/sarasota_2018_2023.csv

# Generate predictions
python src/predict.py --model models/random_forest.pkl --date 2024-01-15

# Evaluate model performance
python src/evaluate.py --model models/random_forest.pkl --test_data data/processed/test_2023.csv
```

## Key Findings

1. **Bloom Persistence Dominates**: Recent bloom history (7-14 day lags) provides 80% of predictive power
2. **Environmental Variables Underperform**: Satellite-derived SST, chlorophyll, and light attenuation contribute <5% despite ecological importance
3. **High Detection Rates**: XGBoost missed only 8 of 281 actual bloom events (97.2% recall)
4. **Operational Viability**: Models achieve >90% accuracy suitable for early warning systems

## Technologies Used

- **Python 3.9+**
- **Machine Learning**: scikit-learn, XGBoost, TensorFlow/Keras
- **Data Processing**: pandas, numpy, xarray, netCDF4
- **Visualization**: matplotlib, seaborn, plotly
- **Geospatial**: geopandas, rasterio

## Future Work

- Incorporate additional physical oceanographic variables (wind, currents, salinity, nutrients)
- Test lagged environmental features (1-4 weeks prior conditions)
- Develop multi-step-ahead forecasting (3, 7, 14 days ahead)
- Expand geographic scope to other Florida coastal regions
- Deploy as real-time operational forecasting system


## Contact

Melita Madhurza - madhu22m@mtholyoke.edu

Data Science Capstone Project - Fall 2025
Professor Arie Shaus, Mount Holyoke College

## Acknowledgments

- Florida Fish & Wildlife Conservation Commission for HAB monitoring data
- NASA Ocean Color Biology Processing Group for MODIS data
- NOAA CoastWatch for sea surface temperature data
- Professor Arie Shaus for guidance and mentorship
```

## Compact One-Liner (for social media/quick sharing):
```
ML models predicting daily red tide blooms in Sarasota Bay with 91.8% accuracy using satellite data + monitoring records. Random Forest + XGBoost achieve 96-97% recall. Data Science Capstone 2025.
```

## Tags/Topics for GitHub:
```
machine-learning
harmful-algal-blooms
oceanography
environmental-science
remote-sensing
time-series-forecasting
random-forest
xgboost
lstm
python
data-science
coastal-management
red-tide
karenia-brevis
satellite-imagery
nasa-modis
predictive-modeling
capstone-project
