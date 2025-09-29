# Electric Vehicle Adoption Impact Analysis: CO2 Emissions Reduction Sensitivity Study

## Executive Summary

This analysis examines the potential impact of widespread electric vehicle (EV) adoption on CO2 emissions across countries using a machine learning approach. By simulating a scenario where 50% of the population in each country adopts EVs, we quantify the emission reduction potential and identify key drivers of environmental impact.

**Important Note:** This analysis is limited to a small number of countries due to data availability constraints. The findings should be interpreted within this context of limited geographic coverage. The data set also includes data from different sources which can impact on the results validation. 

**Key Findings:**
- The model achieved an R² of 0.8813, indicating strong predictive capability
- **High Initial Adoption → Strong Marginal Impact**: Norway (22.5% EV adoption rate) shows the largest improvement with -1.416 tons CO₂ per capita reduction
- **Moderate Adoption → Noticeable Gains**: Netherlands (6.82%), Sweden (8.30%), and Switzerland (4.15%) see clear benefits
- **Low Adoption → Minimal Impact**: United States (1.08%), Italy (0.89%), and Spain (1.00%) show very small percentage changes
- **Counterintuitive Cases**: Poland and Greece slightly increase CO₂ emissions due to coal-heavy electricity grids
- **Critical Insight**: Main hypothesis is that EVs only reduce emissions when power generation is decarbonized



## 1. Model Integration and Key Indicators

### 1.1 Integrated Indicators

The analysis incorporates multiple relevant indicators to create a comprehensive model:

**Vehicle-Related Indicators:**
- **EV Adoption Rate**: Current percentage of EVs in total vehicle fleet
- **Total Cars per Country**: Absolute number of vehicles in each country
- **Vehicles per Capita**: Calculated as total cars divided by population

**Energy Mix Indicators:**
- **Renewable Energy Consumption**: Percentage of total final energy consumption from renewable sources
- **Energy Use per Capita**: Total energy consumption in kg of oil equivalent per capita
- **Electric Power Consumption**: kWh per capita electricity usage

**Economic and Demographic Indicators:**
- **GDP Growth**: Annual percentage growth in gross domestic product
- **Urban Population Growth**: Annual percentage growth in urban population

### 1.2 Model Performance

The linear regression model demonstrates strong predictive capability:
- **R² Score**: 0.8813 (88.13% of variance explained)
- **RMSE**: 1.0969 (root mean square error in CO2 emissions per capita)



## 2. Sensitivity Analysis: 50% EV Adoption Scenario

### 2.1 Methodology

The sensitivity analysis simulates a scenario where 50% of the vehicle fleet in each country consists of electric vehicles. This represents a significant increase from current adoption rates, which vary widely across countries.

**Simulation Process:**
1. **Baseline Prediction**: Use current EV adoption rates to predict CO2 emissions
2. **Scenario Prediction**: Set EV adoption rate to 50% for all countries
3. **Impact Calculation**: Compare predicted emissions between scenarios


### 2.2 Key Assumptions

- **Grid Decarbonization**: Assumes electricity grid becomes cleaner over time
- **Behavioral Changes**: No significant changes in driving patterns or vehicle usage
- **Technology Adoption**: 50% adoption is achievable across all countries regardless of current infrastructure


## 3. Country-Specific Analysis: EV Adoption Impact Patterns

### 3.1 High Initial Adoption → Strong Marginal Impact

**Norway (22.5% EV adoption rate)** demonstrates the most significant improvement:
- **Change_abs**: -1.416 tons CO₂ per capita 
- **Key Factor**: Clean electricity grid amplifies the effect of EVs
- **Implication**: Countries with high renewable energy penetration see exponential benefits from EV adoption

### 3.2 Moderate Adoption → Noticeable Gains

**Netherlands (6.82%), Sweden (8.30%), and Switzerland (4.15%)** show clear benefits:
- These countries are transitioning from fossil fuels while maintaining moderate renewable energy levels
- Moderate adoption rates still yield measurable emission reductions
- Clean energy transition is progressing alongside EV adoption

### 3.3 Low Adoption → Minimal Impact

**United States (1.08%), Italy (0.89%), and Spain (1.00%)** show very small percentage changes


### 3.4 Counterintuitive Cases: Increase in Emissions

**Poland and Greece** slightly increase CO₂ emissions:
- **Hypothesis**: Their electricity grids are coal-heavy, so more EVs increase electricity demand, leading to higher total emissions
- **Critical Insight**: EVs only reduce emissions when power generation is decarbonized


## 4. Assumptions and Limitations

### 4.1 Model Assumptions

**Data Quality Assumptions:**
- **Temporal Consistency**: All indicators from 2022 represent current conditions
- **Cross-Country Comparability**: Indicators are comparable across different countries
- **Limited Geographic Coverage**: Analysis restricted to countries with complete data availability

**Technical Assumptions:**
- **Linear Relationships**: Model assumes linear relationships between variables
- **Independence**: Variables are treated as independent predictors
- **Stationarity**: Relationships remain constant over time

### 4.2 Key Limitations

**Data Limitations:**
1. **Temporal Scope**: Analysis limited to 2022 data, may not capture long-term trends
2. **Country Coverage**: Not all countries have complete data for all indicators
3. **EV Data Quality**: EV adoption rates may be underestimated in some regions
4. **Limited Sample Size**: Analysis covers only a small number of countries due to data availability constraints
5. **Geographic Bias**: Results may not be representative of global patterns due to limited country coverage


