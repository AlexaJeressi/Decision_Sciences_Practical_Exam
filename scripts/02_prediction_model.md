# CO2 Emissions Prediction Model: Analysis and Results

## Model Choice and Methodology

### 1. Model Assumptions

#### **Data Quality Assumptions**
- **Linear Interpolation**: Missing values were filled using linear interpolation within countries across time periods, assuming smooth temporal trends
- **Data Completeness**: Countries with >17% missing data were excluded to ensure reliable model training


#### **Economic Assumptions**
- **Ceteris Paribus**: Other factors affecting CO2 emissions remain constant during GDP growth shocks
- **Linear Relationships**: Economic variables exhibit linear relationships with environmental outcomes
- **Country Fixed Effects**: Unobserved country-specific characteristics remain stable over time




### 2. Model Selection Rationale

**Linear Regression with Country Fixed Effects** was chosen as the primary modeling approach for several key reasons:

- **Country Fixed Effects**: Captures unobserved country-specific characteristics (institutional factors, cultural attitudes, policy frameworks)
- **Temporal Split**: Uses historical data (1995-2020) for training and recent data (2021-2024) for testing, ensuring realistic performance assessment
- **Feature Selection**: Lasso regression automatically identifies the most predictive variables, reducing overfitting
- **Cross-Validation**: 5-fold cross-validation ensures robust model selection and prevents overfitting to specific data patterns



#### **Alternative Models Considered**
- **Random Forest**: Rejected due to lack of interpretability for policy analysis


### 2. Feature Selection Process

#### **Final Model Variables**
The best-performing model (R² = 0.948, RMSE = 1.36) includes:
1. **GDP Growth Rate** (always included for simulation purposes)
2. **Coal Electricity Production** (% of total)
3. **Energy Use per Capita** (kg oil equivalent)
4. **Fossil Fuel Energy Consumption** (% of total)


### 3. Model Performance

#### **Cross-Validation Results**
- **R² Score**: 0.948 (94.8% of variance explained)
- **RMSE**: 1.36 (low prediction error)
- **Temporal Validation**: Strong performance on out-of-sample data (2021-2024)
- **5-Fold CV**: Robust model selection with consistent performance across different data splits



## Scenario Analysis

### 1. Simulation Design

#### **Scenario Description**
- **Shock**: 10 percentage point increase in GDP growth rate
- **Baseline**: Current GDP growth rates (2024 data)
- **Countries**: 20 countries (10 developed, 10 developing)
- **Other Variables**: Held constant at 2024 levels


#### **Rationale for 10% GDP Growth Shock**
- **Policy Relevance**: Represents a significant but realistic economic stimulus
- **Comparative Analysis**: Allows comparison between developed and developing countries


### 2. Country Selection

#### **Developed Countries (10)**
- United States, Germany, United Kingdom, France, Japan, Italy, Spain, Canada, Australia, New Zealand


#### **Developing Countries (10)**
- India, Mexico, Brazil, China, Indonesia, Turkey, Argentina, Chile, South Africa, Korea, Rep.


## Results Interpretation

#### **Differential Impact by Development Level**

**Developed Countries:**
- **Percentage Change Range**: 0.86% to 3.29%
- **Mean Impact**: ~2.1% increase in CO2 emissions
- **Notable Examples**:
  - France: 3.29% increase (highest among developed)
  - United States: 0.89% increase (lowest among developed)

**Developing Countries:**
- **Percentage Change Range**: 1.18% to 7.76%
- **Mean Impact**: ~4.2% increase in CO2 emissions
- **Notable Examples**:
  - India: 7.76% increase (highest overall)
  - China: 2.06% increase (lowest among developing)



#### **Economic Interpretation**

**Why Developing Countries Show Higher Sensitivity:**

1. **Energy Mix Dependence**:
   - Higher reliance on coal and fossil fuels
   - Less diversified energy portfolios
   - Limited renewable energy infrastructure

2. **Economic Structure**:
   - More energy-intensive industrial sectors
   - Less efficient production processes
   - Limited access to clean technologies

3. **Policy Framework**:
   - Weaker environmental regulations
   - Limited carbon pricing mechanisms
   - Less developed green technology sectors



#### **Model Limitations**
- **Static Analysis**: Does not account for dynamic responses or policy changes
- **Linear Assumptions**: May not capture non-linear relationships at extreme values
- **Interpolation Bias**: Linear interpolation may not capture sudden changes or structural breaks in data


