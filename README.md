## [data](data)
Cleaning all raw data

## [docs](docs)
Project related documents

## [src/processing](src/processing)
Raw data were collected and cleaned from 8 different sources under [data](data) folder, each subfolder indicates data source. Integrated data go through  Exploratory Data Analysis to explain data in detail, then Features Selection to reduce dimensionality of data for Modeling step. 

### Data Integration

| Data Abbr | Data | Source | Level | Shape |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| [CCD, NCES](https://nces.ed.gov/ccd/elsi/tableGenerator.aspx) | Common Core of Data | National Center for Education Statistics | District | (1189, 66) |
| [STAAR, TEA](https://tea.texas.gov/student-assessment/testing/staar/staar-aggregate-data) | State of Texas Assessments of Academic Readiness for 2018-2019 and 2020-2021 | Texas Education Agency | District | (1184, 217) (1182, 217) |
| [LAUS, BLS](https://www.bls.gov/lau/##cntyaa) | Local Area Unemployment Statistics | U.S. Bureau of Labor Statistics | County | (254, 13) |
| [Census Bureau](https://schoolsdata2-93b5c-tea-texas.opendata.arcgis.com/datasets/census-block-group-2010-tx/) | Census Block Group 2010 | Census Bureau | County | (254, 37) |
| [Covid, DSHS](https://dshs.texas.gov/coronavirus/schools/texas-education-agency/) | Texas Public Schools COVID-19 Data | Texas Department of State Health Services | District | (1216, 7) |
| [Covid, USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/state/texas) | Texas Coronavirus Cases and Deaths | USAFacts | County | (254, 8) |
| [ADA, TEA](https://tea.texas.gov/finance-and-grants/state-funding/state-funding-reports-and-data/average-daily-attendance-and-wealth-per-average-daily-attendance) | Average Daily Attendance | Texas Education Agency | District | (1226, 3) |
| [ESSER, TEA](https://tea.texas.gov/finance-and-grants/grants/grants-administration/applying-for-a-grant/entitlements) | Elementary and Secondary School Emergency Relief | Texas Education Agency | District | (1208, 6)  |
- [Data_Integration.ipynb](src/processing/Data_Integration.ipynb): All cleaned data are integrated into single dataframe and processed as below
  1. Normalization: Normalizing numberical data into a percentage.
  2. Calculating Delta: Getting differences for the important variables having both values for 2018-2019 and 2020-2021
  3. Labeling: Creating 3 classes for Learning Loss: Loss, Expected, Gain
- Exporting: Generating 3 versions of csv
  - DATA_Texas_District_v1.csv: raw integrated data with normalization, delta without missing value handling for EDA
  - DATA_Texas_District_v2.csv: dropping all missing values with normalization and delta values for Feature Selection and Baseline modeling
  - DATA_Texas_District_v3.csv: raw integrated data without normalization, delta. missing value handling for Gradient Boosting experiment

### Exploratory Data Analysis
- [EDA.ipynb](src/processing/EDA.ipynb)
   - Locale
   - Poverty Proxy: Ttile 1, Free or Reduced Lunch elibility
   - Race/Ethnicity
   - Enrollment by Grades
   - Covid: On-Campus, Infection and Deaths Rates
   - ADA: Average Daily Attendance
   - STAAR: Tested Students, Learning Loss
   - Census Block Group 2010: Race/Ethnicity, Gender, Age Group, Households, and Housing Units
   - ESSER: Amount of each grant allocation

### Feature Selection
9 methods were used to score feature importance automatically and select the best features predicting Learning Loss for [Feature_Selection_Math.ipynb](src/processing/Feature_Selection_Math.ipynb) and [Feature_Selection_Reading.ipynb](src/processing/Feature_Selection_Reading.ipynb):
* Filter Methods
	* Variance Threshold
* Embedded Methods
	* L1 Regularized Logistic Regression (Lasso)
	* Random Forest Feature Importance
* Wrapper Methods
	* Recursive Feature Elimination (RFE) with Random Forest
	* Recursive Feature Elimination (RFE) with Ridge Regression
	* Permutation Importance with Random Forest
	* Permutation Importance with Ridge Regression
	* Sequential Feature Selection (SFS) with KNN
	* Sequential Feature Selection (SFS) with Ridge Regression

## [src/modeling](src/modeling)
Prediction modeling on Learning Loss due to COVID-19 in math and reading go through 3 phases: State-of-an-art modeling, Gradient boosting modeling, and Gradient boosting experimenting with missing values. First two phases compare 10 feature sets selected from [Feature_Selection_Math.ipynb](src/processing/Feature_Selection_Math.ipynb) and [Feature_Selection_Reading.ipynb](src/processing/Feature_Selection_Reading.ipynb), and the last phase experiments with raw data containing missing values.

### State-of-an-art modeling 
* 5 models were trained to predict Learning Loss in [Modeling_BL_Math.ipynb](src/modeling/Modeling_BL_Math.ipynb) and [Modeling_BL_Reading.ipynb](src/modeling/Modeling_BL_Reading.ipynb)
  * Ridge Regression
  * SVM (Linear, Kernel)
  * KNN
  * Random Forest
  * Grandient Boosting

### Advanced gradient boosting modeling 
* 4 models were trained to predict Learning Loss in [Modeling_GB_Math.ipynb](src/modeling/Modeling_GB_Math.ipynb) and [Modeling_GB_Reading.ipynb](src/modeling/Modeling_GB_Reading.ipynb) 
  * XGBoost
  * LightGBM
  * CatBoost
  * HistGradientBoost

### Experimenting Advanced gradient boosting modeling with missing values
* The same 4 gradient boosting models were trained to predict Learning Loss using raw data with missing values in [Modeling_NA_GB_Math.ipynb](src/modeling/Modeling_NA_GB_Math.ipynb) and [Modeling_NA_GB_Reading.ipynb](src/modeling/odeling_NA_GB_Reading.ipynb) 
