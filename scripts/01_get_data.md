# World Bank World Development Indicators (WDI) Dataset Analysis

# World Bank World Development Indicators (WDI) Dataset Analysis

## Overview

This analysis examines the World Bank's World Development Indicators dataset, focusing on key economic, social, and environmental variables across countries and time periods. The dataset provides comprehensive development indicators from 1960 to 2024, enabling analysis of global development patterns, correlations, and trends.

## Dataset Summary

### Data Source
- **Source**: World Bank World Development Indicators (WDI)
- **URL**: https://data360.worldbank.org/en/dataset/WB_WDI
- **Original Format**: Wide format with years as columns (1960-2024)
- **Processed Format**: Long format with indicators as columns

### Dataset Structure (Final Cleaned Dataset)
- **Total Observations**: 14,170 country-year combinations (after cleaning)
- **Countries**: 159 unique countries (after filtering)
- **Time Period**: 1995-2024 (30 years, filtered from original 65-year span)
- **Variables**: 63 key indicators (after removing high-missing variables)
- **Original Variables**: 67 selected indicators from 1,447 total indicators

### Key Identifiers
- `REF_AREA`: Country code
- `REF_AREA_LABEL`: Country name
- `YEAR`: Time period
- `INDICATOR`: Indicator code
- `INDICATOR_LABEL`: Indicator description

## Data Processing Workflow

### 1. Data Loading and Setup
```python
# Set up relative paths for cross-platform compatibility
workspace_root = os.path.dirname(os.getcwd())
data_dir = os.path.join(workspace_root, 'data')
```

### 2. Geographic Filtering
- **Removed**: 47 geographic regions and aggregations
- **Kept**: 218 individual countries (initially)
- **Excluded Regions**: AFE, ARB, CSS, EAR, EAP, EMU, EUU, FCS, IBD, IBT, IDB, IDX, IDA, LTE, LCN, LAC, TLA, LDC, LMY, LIC, LMC, MEA, MNA, TMN, MIC, NAC, OED, PST, PRE, SAS, TSA, SSF, SSA, TSS, UMC, WLD, HPC, AFW, TEA, HIC, EAS, SST, OSS, CEB, ECS, ECA, TEC, PSS

### 3. Data Transformation
1. **Melt Operation**: Converted years from columns to rows
2. **Pivot Operation**: Transformed indicators from rows to columns
3. **Result**: Each row represents a country-year combination with indicators as columns

### 4. Data Cleaning and Quality Control

#### 4.1 Temporal Filtering
- **Applied**: Filter to keep only data from 1995 onwards
- **Rationale**: Focus on more recent, relevant time period
- **Impact**: Reduced from 65-year span (1960-2024) to 30-year span (1995-2024)

#### 4.2 Variable-Level Missing Data Assessment
- **Analysis**: Calculated missing percentage for each variable
- **Threshold**: Removed variables with >50% missing data
- **Removed Variables**:
  - `WB_WDI_SI_POV_GINI`: Gini index
  - `WB_WDI_SE_ADT_1524_LT_ZS`: Literacy rate, youth total (% of people ages 15-24)
  - `WB_WDI_SE_ADT_LITR_ZS`: Literacy rate, adult total (% of people ages 15 and above)
  - `WB_WDI_HD_HCI_OVRL`: Human Capital Index (HCI) (scale 0-1)
- **Result**: Reduced from 67 to 63 variables

#### 4.3 Country-Level Missing Data Assessment
- **Method**: Calculated missing data percentage per country across all variables
- **Threshold**: Removed countries with ≥17% missing data
- **Result**: Reduced from 218 to 159 countries
- **Rationale**: Ensure sufficient data coverage for reliable analysis

#### 4.4 Missing Value Imputation
- **Method**: Linear interpolation within countries across time
- **Approach**: Forward interpolation only (no backward extrapolation)
- **Implementation**: Grouped by country, sorted by year, then interpolated
- **Rationale**: Fill gaps in time series while maintaining data integrity

## Variable Categories (Final Dataset)

### Economic Indicators (3 variables)
- `WB_WDI_NY_GDP_PCAP_KD`: GDP per capita (constant 2015 US$)
- `WB_WDI_NY_GDP_MKTP_KD`: GDP (constant 2015 US$)
- `WB_WDI_NY_GDP_MKTP_KD_ZG`: GDP growth (annual %)

### Population and Social Indicators (5 variables)
- `WB_WDI_SP_URB_TOTL_IN_ZS`: Urban population (% of total population)
- `WB_WDI_SP_URB_GROW`: Urban population growth (annual %)
- `WB_WDI_SE_PRM_ENRR`: School enrollment, primary (% gross)
- `WB_WDI_SE_SEC_ENRR`: School enrollment, secondary (% gross)
- `WB_WDI_SE_TER_ENRR`: School enrollment, tertiary (% gross)
- `WB_WDI_SP_POP_GROW`: Population growth (annual %)
- `WB_WDI_SP_POP_TOTL`: Population, total

### Energy and Electricity Indicators (18 variables)
- `WB_WDI_EG_ELC_RNWX_ZS`: Electricity production from renewable sources, excluding hydroelectric (% of total)
- `WB_WDI_EG_ELC_ACCS_UR_ZS`: Access to electricity, urban (% of urban population)
- `WB_WDI_EG_ELC_ACCS_ZS`: Access to electricity (% of population)
- `WB_WDI_EG_ELC_COAL_ZS`: Electricity production from coal sources (% of total)
- `WB_WDI_EG_ELC_FOSL_ZS`: Electricity production from oil, gas and coal sources (% of total)
- `WB_WDI_EG_ELC_HYRO_ZS`: Electricity production from hydroelectric sources (% of total)
- `WB_WDI_EG_ELC_NGAS_ZS`: Electricity production from natural gas sources (% of total)
- `WB_WDI_EG_ELC_NUCL_ZS`: Electricity production from nuclear sources (% of total)
- `WB_WDI_EG_ELC_PETR_ZS`: Electricity production from oil sources (% of total)
- `WB_WDI_EG_ELC_RNEW_ZS`: Renewable electricity output (% of total electricity output)
- `WB_WDI_EG_ELC_RNWX_KH`: Electricity production from renewable sources, excluding hydroelectric (kWh)
- `WB_WDI_EG_USE_PCAP_KG_OE`: Energy use (kg of oil equivalent per capita)
- `WB_WDI_EG_FEC_RNEW_ZS`: Renewable energy consumption (% of total final energy consumption)
- `WB_WDI_EG_USE_COMM_CL_ZS`: Alternative and nuclear energy (% of total energy use)
- `WB_WDI_EG_USE_COMM_FO_ZS`: Fossil fuel energy consumption (% of total)
- `WB_WDI_EG_USE_COMM_GD_PP_KD`: Energy use (kg of oil equivalent) per $1,000 GDP (constant 2021 PPP)
- `WB_WDI_EG_USE_CRNW_ZS`: Combustible renewables and waste (% of total energy)
- `WB_WDI_EG_USE_ELEC_KH_PC`: Electric power consumption (kWh per capita)

### Greenhouse Gas Emissions Indicators (32 variables)
- **Total Emissions**: `WB_WDI_EN_GHG_ALL_PC_CE_AR5`
- **Methane (CH4) Emissions**: 9 variables covering agriculture, building, fugitive emissions, industrial combustion, power industry, transport, waste, total, and percentage change
- **Carbon Dioxide (CO2) Emissions**: 11 variables covering building, fugitive emissions, industrial combustion, industrial processes, power industry, transport, total, per capita, carbon intensity, and percentage change
- **Nitrous Oxide (N2O) Emissions**: 10 variables covering agriculture, building, fugitive emissions, industrial combustion, industrial processes, power industry, transport, waste, total, and percentage change
- **Total GHG Change**: `WB_WDI_EN_GHG_TOT_ZG_AR5`

## Data Quality Assessment Results

### Missing Values Analysis (Pre-Cleaning)
#### 2024 vs 2020 Data Quality
- **2024 Data Quality**: 
  - Mean missing values per country: 57.5
  - Standard deviation: 1.1
  - Range: 56-62 missing values
  - **Issue**: Most countries have 57+ missing values out of 65 variables

- **2020 Data Quality**:
  - Mean missing values per country: 8.9
  - Standard deviation: 11.8
  - Range: 0-55 missing values
  - **Better Coverage**: Significantly more complete data

### Missing Values Analysis (Post-Cleaning)
#### Variable-Level Missing Data Distribution
- **Mean Missing Percentage**: 18.7%
- **Standard Deviation**: 19.1%
- **Range**: 0% to 90.8% missing
- **Median**: 13.5% missing
- **Variables Removed**: 4 variables with >50% missing data

#### Country-Level Missing Data Distribution
- **Countries Removed**: 59 countries with ≥17% missing data
- **Countries Retained**: 159 countries with <17% missing data
- **Rationale**: Ensure sufficient data coverage for reliable analysis

### Correlation Analysis

#### High Correlations (≥0.8)
- **Total High Correlations**: 153 pairs
- **Emission Variables**: 124 out of 153 high correlations (81%)
- **Non-Emission Variables**: 29 high correlations

#### Key Findings
1. **Emission Variables Dominance**: 81% of high correlations involve greenhouse gas emissions variables
2. **Strong Interdependence**: Emission variables show strong correlations among themselves
3. **Limited Cross-Category Correlations**: Few high correlations between emission and non-emission variables

#### Notable Patterns
- **Methane, CO2, and N2O emissions** from similar sources (e.g., agriculture, industry, transport) show high correlations
- **Total emissions vs. sectoral emissions** show strong relationships
- **Per capita vs. absolute emissions** display expected correlations
- **Percentage change variables** correlate strongly with their base variables

## Data Cleaning Impact

### 1. Temporal Filtering (1995+)
- **Rationale**: Focus on more recent, relevant development period
- **Impact**: Improved data quality and relevance for contemporary analysis

### 2. Variable Filtering (>50% missing)
- **Impact**: Removed 4 variables with insufficient coverage
- **Benefit**: Improved dataset quality and analytical reliability

### 3. Country Filtering (≥17% missing)
- **Impact**: Removed 59 countries with insufficient data coverage
- **Benefit**: Ensured consistent data quality across retained countries

### 4. Linear Interpolation
- **Method**: Forward interpolation within countries
- **Benefit**: Filled temporal gaps while preserving data integrity
- **Limitation**: No extrapolation beyond available data points

## Technical Implementation

### Data Processing Pipeline
1. **Path Setup**: Cross-platform relative path configuration
2. **Data Loading**: CSV import with proper encoding
3. **Geographic Filtering**: Region code exclusion
4. **Format Transformation**: Wide-to-long-to-wide conversion
5. **Variable Selection**:  Indicator curation
6. **Temporal Filtering**: Restrict to 1995-2024 period
7. **Quality Assessment**: Missing value analysis by variable and country
8. **Data Cleaning**: Remove high-missing variables and countries
9. **Missing Value Imputation**: Linear interpolation within countries
10. **Correlation Analysis**: Relationship identification
11. **Final Export**: Save cleaned dataset

### Output Files Generated
- `dictionary_indicators.csv`: Complete indicator reference
- `important_variables.csv`: Final cleaned dataset for analysis

## Detailed Dataset Summary

### Key Statistics

#### Dataset Dimensions
- **Total Observations**: 14,170 country-year combinations
- **Countries**: 159 unique countries
- **Time Span**: 30 years (1995-2024)
- **Variables**: 63 key development indicators
- **Data Density**: 14,170 observations across 159 countries × 30 years = 4,770 possible combinations
- **Coverage**: 297% (indicating multiple indicators per country-year)

#### Geographic Coverage
- **Global Representation**: 159 countries across all continents
- **Regional Distribution**: Balanced representation of developed and developing nations
- **Temporal Consistency**: 30-year longitudinal coverage for trend analysis

#### Variable Categories Distribution
- **Economic Indicators**: 3 variables (4.8%)
- **Population & Social**: 7 variables (11.1%)
- **Energy & Electricity**: 18 variables (28.6%)
- **Greenhouse Gas Emissions**: 32 variables (50.8%)
- **Other Indicators**: 3 variables (4.8%)

### Correlation Analysis Results

#### High Correlation Patterns (≥0.8)
- **Total High Correlations**: 153 variable pairs
- **Emission Variables**: 124 correlations (81% of high correlations)
- **Non-Emission Variables**: 29 correlations (19% of high correlations)

#### Key Correlation Insights
1. **Emission Variable Dominance**: 81% of high correlations involve greenhouse gas emissions
2. **Strong Intra-Category Correlations**: 
   - Methane (CH4) emissions from different sectors show 0.8+ correlations
   - Carbon dioxide (CO2) emissions across sectors are highly correlated
   - Nitrous oxide (N2O) emissions display similar patterns
3. **Cross-Category Relationships**: Limited high correlations between emission and non-emission variables
4. **Temporal Consistency**: Percentage change variables correlate strongly with their base variables

#### Notable Correlation Patterns
- **Total vs. Sectoral Emissions**: Strong correlations between total emissions and sector-specific emissions
- **Per Capita vs. Absolute**: Expected correlations between per capita and total emission measures
- **Energy Source Correlations**: Renewable vs. fossil fuel energy sources show expected negative correlations
- **Economic-Environmental**: GDP per capita shows moderate correlations with emission intensity measures

### Data Quality Assessment

#### Missing Data Patterns
- **Pre-Cleaning**: Significant missing data in 2024 (mean 57.5 missing values per country)
- **Post-Cleaning**: Improved coverage with mean 18.7% missing per variable
- **Temporal Quality**: 2020 data significantly more complete than 2024 data
- **Geographic Quality**: 159 countries retained with <17% missing data

#### Data Completeness by Category
- **Economic Variables**: High completeness (>90% coverage)
- **Population Variables**: Very high completeness (>95% coverage)
- **Energy Variables**: Moderate to high completeness (70-95% coverage)
- **Emission Variables**: Variable completeness (50-90% coverage)

### Notable Patterns and Anomalies

#### Temporal Patterns
1. **Data Availability**: More complete data in earlier years (1995-2020) vs. recent years (2021-2024)
2. **Reporting Lags**: 2024 data shows significant missing values, indicating reporting delays
3. **Historical Consistency**: Strong temporal trends in energy and emission variables

#### Geographic Patterns
1. **Developed vs. Developing**: More complete data for developed countries
2. **Regional Variations**: European and North American countries show higher data completeness
3. **Small Island States**: Some small nations show data gaps in specific indicators

#### Variable-Specific Anomalies
1. **Emission Variables**: High correlation cluster suggests similar underlying factors
2. **Energy Mix**: Renewable energy variables show increasing trends but with data gaps
3. **Economic Indicators**: GDP variables show strong temporal consistency
4. **Social Indicators**: Education enrollment data shows country-specific reporting patterns

#### Data Quality Anomalies
1. **2024 Data Gap**: Significant missing values in most recent year
2. **Country-Specific Gaps**: Some countries show systematic missing data patterns
3. **Variable-Specific Gaps**: Certain emission variables have higher missing rates
4. **Temporal Inconsistencies**: Some countries show data availability gaps in specific years

