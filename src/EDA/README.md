

# Data Integration

- Raw data were collected and cleaned under [data](../../data) folder, each subfolder indicates data source.
  - [NCES](../../data/nces): 
    - DATA_NCES_DISTRICT.csv
  - [STAAR](../../data/staar):
    - DATA_STAAR_DISTRICT_2019.csv
    - DATA_STAAR_DISTRICT_2021.csv
  - [Covid](../../data/covid):
    - DATA_COVID_DISTRICT.csv
    - DATA_COVID_COUNTY.csv
  - [LAUS](../../data/laus):
    - DATA_LAUS_COUNTY.csv
  - [ADA](../../data/ada):
    - DATA_ADA_DISTRICT.csv
- [Task1_Data_Integration.ipynb](CHERR/EDA/Task1_Data_Integration.ipynb): All cleaned data are integrated into [`DATA_Texas_District.csv`](https://git.txstate.edu/DataLab/data-NCES/blob/master/CHERR/EDA/DATA_Texas_District.csv):

# Exploratory Data Analysis

- [Task2_EDA.ipynb](CHERR/EDA/Task2_EDA.ipynb)
  1. Normalization: Normalizing numberical data into a percentage.
  2. Calculating Delta: Getting differences for the important variables having both values for 2018-2019 and 2020-2021
  3. Labeling: Creating 5 classes for Learning Loss
  4. EDA
     - Locale
     - Poverty Proxy: Ttile 1, Free or Reduced Lunch elibility
     - Race/Ethnicity
     - Enrollment by Grades
     - Covid: On-Campus, Infection and Deaths Rates
     - ADA: Average Daily Attendance
     - STAAR: Tested Students, Learning Loss
  5. Data Cleaning for ML Modeling: Dropping instances with missing values or redundant columns for modeling. The data with no empty values is saved as  [`DATA_Texas_District_ML.csv`](https://git.txstate.edu/DataLab/data-NCES/blob/master/CHERR/EDA/DATA_Texas_District_ML.csv).

# Feature Selection

- [Task3_Feature_Selection_Math.ipynb](CHERR/EDA/Task3_Feature_Selection_Math.ipynb) - finding the best feature set for Math subject
- [Task3_Feature_Selection_Reading.ipynb](CHERR/EDA/Task3_Feature_Selection_Reading.ipynb) - finding the best feature set for Reading subject

4 different feature selection methods with a combinatino with ML models are used to see the best feature set for predictiong Learning Loss on Math and Reading subjects separately. Accuracy(Test set) and MCC score are used for evaluation. 
* L1 Regularized Logistic Regression (Lasso)
* Random Forest Feature Importance
* Permutation Importance 
  * with Gradient Boosting
  * with Random Forest
* Recursive Feature Elimination (RFE)
  * with Ridge Regression
  * with Random Forest
* Sequential Feature Selection (SFS)
  * with Ridge Regression
  * with KNN



