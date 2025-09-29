# Decision Sciences Practical Exam: CO2 Emissions and EV Adoption Analysis

This repository contains a comprehensive analysis of CO2 emissions patterns and electric vehicle (EV) adoption across countries, using World Bank Development Indicators (WDI) data and vehicle statistics. The project explores the relationship between economic development, energy consumption, and environmental impact.

## Project Overview

1. Data Processing & Preparation  
   - Notebook: 01_get_data.ipynb  
   - Report: 01_get_data.md  
   - Description: Extracts and processes World Bank indicators and vehicle adoption data, cleaning and preparing it for analysis.

2. CO2 Emissions Prediction Model  
   - Notebook: 02_prediction_model.ipynb  
   - Report: 02_prediction_model.md  
   - Description: Builds and evaluates a predictive model for CO2 emissions based on economic and energy variables.

3. EV Adoption Impact Analysis  
   - Notebook: 03_ev_adoption.ipynb  
   - Report: 03_ev_adoption.md  
   - Description: Analyzes how the growth of electric vehicle adoption influences CO2 emissions trends.

4. Classifier Analysis  
   - Notebook: 04_classifier.ipynb  
   - Report: 04_classifier_analysis.md  
   - Description: Implements and evaluates classification models to categorize countries based on their emissions and adoption patterns.



## Project Structure

```
Decision_Sciences_Practical_Exam/
├── data/                           # Data files
│   ├── important_variables.csv    # Processed WDI data (1995-2024)
│   ├── dictionary_indicators.csv  # Variable definitions
│   ├── cars_country.csv           # EV stock data by country
│   └── cars-by-country-2025.csv   # Total vehicle data by country
├── scripts/                       # Analysis notebooks
│   ├── 01_get_data.ipynb         # Data processing and cleaning
│   ├── 02_prediction_model.ipynb # CO2 emissions prediction model
│   ├── 03_ev_adoption.ipynb # CO2 emissions prediction model
│   └── 04_clasiffier.ipynb       # EV adoption impact analysis
└── README.md                      # This file
```


## Technical Requirements

### Dependencies
- Python 3.8+
- Jupyter Notebook
- pandas
- numpy
- scikit-learn
- matplotlib (for visualization)
