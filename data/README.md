

## Data Sources

Merged district or county level data including [STAAR data](https://tea.texas.gov/student-assessment/testing/staar/staar-aggregate-data), [COVID data](https://dshs.texas.gov/coronavirus/schools/texas-education-agency/), [NCES data](https://nces.ed.gov/ccd/elsi/tableGenerator.aspx), [LAUS data](https://www.bls.gov/lau/#cntyaa) and ADA data. Each dataset was cleaned separately in a corresponding jupyter notebook under the folder. (ie STAAR data was cleaned in staar_district_cleaning.ipynb). Cleaned data was also saved under the same folder with the file name convention, `DATA_[Source]_[District|County].csv` (NCES district data is saved as `DATA_NCES_DISTRICT.csv`)

### [ada](ada): Average Daily Attendance
- [DATA_ADA_DISTRICT.csv](ada/DATA_ADA_DISTRICT.csv): Avaerage Daily Attendance for 2019 and 2021
- Note: Each column in ada_county.csv is sum of ada_district.csv

### [covid](covid): Teaxs Public Schools COVID-19 Data from [Texas Education Agency](https://dshs.texas.gov/coronavirus/schools/texas-education-agency/)
- [DATA_COVID_DISTRICT.csv](covid/DATA_COVID_DISTRICT.csv): District Enrollment, Approx. District On-Campus Enrollment
- [DATA_COVID_COUNTY.csv](covid/DATA_COVID_COUNTY.csv): Confirmed Deaths, Confirmed Cases, County Population

### [laus](laus): Local Area Unemployment Statistics from [U.S. Bureau of Labor Statistics](https://www.bls.gov/lau/#cntyaa)
- [DATA_LAUS_COUNTY.csv](laus/DATA_LAUS_COUNTY.csv): Labor force data including Labor Force, Employed, Unemployment by county, 2019 and 2021 annual averages

### [nces](nces): Common Core Data(CCD) from [National Center for Education Statistics](https://nces.ed.gov/ccd/elsi/tableGenerator.aspx)
- 2021 district data (Table ID: 518944)
- 2019 district data (Table ID: 518943)
- 2019, 2021 grade 3-8 data (Table ID: 518945 for Grade 3-8, 521941 for all grades)
- 2019, 2021 school(campus) data (Table ID: 518946)
- [DATA_NCES_DISTRICT.csv](nces/DATA_NCES_DISTRICT.csv): Integrated all NCES data above including Student Race, Grades, Title 1 & Free/Reduced Lunch Eligibilities

### [staar](staar): State of Texas Assessments of Academic Reainess(STAAR) [Texas Education Agency](https://tea.texas.gov/student-assessment/testing/staar/staar-aggregate-data)
- [DATA_STAAR_DISTRICT_2019.csv](staar/DATA_STAAR_DISTRICT_2019.csv): STAAR Aggregate Level Data for 2018-2019 for Grade 3-8 Math and Reading
- [DATA_STAAR_DISTRICT_2021.csv](staar/DATA_STAAR_DISTRICT_2021.csv): STAAR Aggregate Level Data for 2020-2021 for Grade 3-8 Math and Reading

### Data Integration
All cleaned data are integrated into [DATA_Texas_District.csv](../CHERR/EDA/DATA_Texas_District.csv) from [Task1_Data_Integration.ipynb](../CHERR/EDA/Task1_Data_Integration.ipynb)
