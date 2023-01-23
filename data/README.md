

## Data Sources

Data are collected from the sources below and cleaned separately in a corresponding jupyter notebook under the folder. (ie STAAR data was cleaned in staar_district_cleaning.ipynb). Cleaned data was also saved under the same folder with the file name convention, `DATA_[Source]_[District|County].csv` (NCES district data is saved as `DATA_NCES_DISTRICT.csv`)

### [ada](ada): Average Daily Attendance from [Texas Education Agency](https://tea.texas.gov/finance-and-grants/state-funding/state-funding-reports-and-data/average-daily-attendance-and-wealth-per-average-daily-attendance)
- [DATA_ADA_DISTRICT.csv](ada/DATA_ADA_DISTRICT.csv): Avaerage Daily Attendance for 2019 and 2021
- Note: Each column in ada_county.csv is sum of ada_district.csv

### [census](census): Census Block Group 2010 Texas [Census/TEA](https://schoolsdata2-93b5c-tea-texas.opendata.arcgis.com/datasets/census-block-group-2010-tx)
- [DATA_Census_Block_Group_2010_TX_County.csv](census/DATA_Census_Block_Group_2010_TX_County.csv): demographics county level in Texas 2010

### [covid](covid): COVID-19 Data in Texas
- [DATA_COVID_DISTRICT.csv](covid/DATA_COVID_DISTRICT.csv): District Enrollment, Approx. District On-Campus Enrollment from [DSHS](https://dshs.texas.gov/coronavirus/schools/texas-education-agency/)
- [DATA_COVID_COUNTY.csv](covid/DATA_COVID_COUNTY.csv): Confirmed Deaths, Confirmed Cases, County Population from [UsaFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/state/texas)

### [esser](esser): Elementary and Secondary School Emergency Relief Entitlement from [Texas Education Agency](https://tea.texas.gov/finance-and-grants/grants/grants-administration/applying-for-a-grant/entitlements)
- [DATA_ESSER_DISTRICT.csv](ada/DATA_ESSER_DISTRICT.csv): Allocated amounts of funds in each school district.

### [laus](laus): Local Area Unemployment Statistics from [U.S. Bureau of Labor Statistics](https://www.bls.gov/lau/#cntyaa)
- [DATA_LAUS_COUNTY.csv](laus/DATA_LAUS_COUNTY.csv): Labor force data including Labor Force, Employed, Unemployment by county, 2019 and 2021 annual averages

### [nces](nces): Common Core of Data(CCD) from [National Center for Education Statistics](https://nces.ed.gov/ccd/elsi/tableGenerator.aspx)
- 2021 district data (Table ID: 518944)
- 2019 district data (Table ID: 518943)
- 2019, 2021 grade 3-8 data (Table ID: 518945 for Grade 3-8, 521941 for all grades)
- 2019, 2021 school(campus) data (Table ID: 518946)
- [DATA_NCES_DISTRICT.csv](nces/DATA_NCES_DISTRICT.csv): Integrated all NCES data above including Student Race, Grades, Title 1 & Free/Reduced Lunch Eligibilities

### [staar](staar): State of Texas Assessments of Academic Reainess(STAAR) [Texas Education Agency](https://tea.texas.gov/student-assessment/testing/staar/staar-aggregate-data)
- [DATA_STAAR_DISTRICT_2019.csv](staar/DATA_STAAR_DISTRICT_2019.csv): STAAR Aggregate Level Data for 2018-2019 for Grade 3-8 Math and Reading
- [DATA_STAAR_DISTRICT_2021.csv](staar/DATA_STAAR_DISTRICT_2021.csv): STAAR Aggregate Level Data for 2020-2021 for Grade 3-8 Math and Reading

## Data Integration
All cleaned data are integrated in [Data_Integration.ipynb](../src/processing/Data_Integration.ipynb)
