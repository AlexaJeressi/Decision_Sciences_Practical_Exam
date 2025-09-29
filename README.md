# Decision Sciences Practical Exam: CO2 Emissions and EV Adoption Analysis

This repository contains a comprehensive analysis of CO2 emissions patterns and electric vehicle (EV) adoption across countries, using World Bank Development Indicators (WDI) data and vehicle statistics. The project explores the relationship between economic development, energy consumption, and environmental impact.

## Project Overview

This project consists of three main analytical components:

1. **Data Processing & Preparation** (`01_get_data.ipynb`)
2. **CO2 Emissions Prediction Model** (`02_prediction_model.ipynb`) 
3. **EV Adoption Impact Analysis** (`03_ev_adoption.ipynb`)

## Project Structure

```
Decision_Sciences_Practical_Exam/
├── data/                           # Data files
│   ├── WB_WDI_WIDEF.csv           # World Bank WDI raw data
│   ├── important_variables.csv    # Processed WDI data (1995-2024)
│   ├── dictionary_indicators.csv  # Variable definitions
│   ├── cars_country.csv           # EV stock data by country
│   └── cars-by-country-2025.csv   # Total vehicle data by country
├── scripts/                       # Analysis notebooks
│   ├── 01_get_data.ipynb         # Data processing and cleaning
│   ├── 02_prediction_model.ipynb # CO2 emissions prediction model
│   └── 03_ev_adoption.ipynb       # EV adoption impact analysis
└── README.md                      # This file
```

## Analysis Components

### 1. Data Processing (`01_get_data.ipynb`)
- **Source**: World Bank Development Indicators (WDI) dataset
- **Scope**: 159 countries, 1995-2024 timeframe
- **Key Variables**: 67 economic, demographic, energy, and emissions indicators
- **Data Quality**: 
  - Removed countries with >17% missing data
  - Applied linear interpolation for missing values
  - Filtered out geographic regions (kept only countries)

### 2. CO2 Emissions Prediction Model (`02_prediction_model.ipynb`)
- **Target Variable**: CO2 emissions per capita (`WB_WDI_EN_GHG_CO2_PC_CE_AR5`)
- **Methodology**: 
  - Lasso regression for feature selection
  - Temporal split: train on 1995-2020, test on 2021-2024
  - Country dummy variables for fixed effects
- **Key Predictors**:
  - GDP growth rate
  - Coal electricity production
  - Energy use per capita
  - Fossil fuel consumption
- **Model Performance**: R² = 0.948, RMSE = 1.359

### 3. EV Adoption Impact Analysis (`03_ev_adoption.ipynb`)
- **Data Sources**: 
  - IEA Global EV Data Explorer
  - World Population Review vehicle statistics
- **Analysis Year**: 2022 (most recent comprehensive data)
- **Key Findings**: 
  - EV adoption rate impact on CO2 emissions
  - Simulation of 50% EV adoption scenario
  - Model performance: R² = 0.881, RMSE = 1.097

## Technical Requirements

### Dependencies
- Python 3.8+
- Jupyter Notebook
- pandas
- numpy
- scikit-learn
- matplotlib (for visualization)
