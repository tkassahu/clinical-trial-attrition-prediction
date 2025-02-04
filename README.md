# Predicting Patient Attrition in Clinical Trials

## Project Overview  
This project builds a **machine learning model** to predict **patient attrition percentage** in clinical trials using data extracted from **ClinicalTrials.gov API**. Additionally, it maps participating clinical research facilities **geographically** based on available location data.  

### Objectives  
- **Aim 1:** Develop a **predictive model** to estimate patient dropout percentages in clinical trials.  
- **Aim 2:** Map clinical trial locations **geographically** using **Python** to analyze accessibility and attrition trends.

## Dataset & API  
- **Primary Dataset:** Attrition dataset (`ct_attrition_dataset.csv`) containing **1325 clinical trials** with **NCT numbers and attrition percentage**.  
- **Data Source:** [ClinicalTrials.gov API](https://clinicaltrials.gov/api/v2/studies/NCT04513925)  
- **Additional Data:** [Rural-Urban Commuting Area (RUCA) Codes](https://depts.washington.edu/uwruca/ruca-download.php)  

## Features Used for Model Development  
### Extracted from ClinicalTrials.gov API:  
- **Study Design:** Trial setup, phases, masking information  
- **Eligibility Criteria:** Demographics, mean age, gender ratio  
- **Recruitment Locations:** Hospitals/organizations where patients were recruited  
- **Therapy/Disease Information:** Drugs or treatments being studied  

### Engineered Features:  
- **Number of recruitment locations per trial**  
- **Clinical trial duration (start to completion date)**  
- **Trial phase (Phase 1, 2, 3, or 4)**  
- **Serious adverse events reported**  
- **RUCA classification (Urban vs. Rural trials)**  

## Machine Learning Models & Results  
Two machine learning models were used for predictive modeling:  

### XGBoost Regressor:  
- **R² Score:** 0.33  
- **RMSE:** 8.67  
- **Top Features:** **Trial Duration, Locations, Enrollment Info, Serious Events**  

### Random Forest Regressor:  
- **R² Score:** 0.31  
- **RMSE:** 8.79  
- **Top Features:** **Trial Duration, Serious Events, Enrollment Info, Locations**  

### Key Insights:  
- **Trial Duration** was the strongest predictor of attrition.  
- **Serious Adverse Events** increased dropout rates.  
- **Enrollment Size** correlated with attrition (larger trials had more dropouts).  
- **Geographic factors (locations)** impacted attrition, highlighting accessibility issues.  

## Geocoding & Mapping Clinical Trials  
- Extracted facility locations (latitude, longitude) using:  
  - **ClinicalTrials.gov API**  
  - **Zip Code Database (`pyzipcode` package)**  
- **Mapping Tool:** `folium` for **interactive visualization**  
- **Color-coded density map** based on attrition rates  

## How to Run the Code  
### 1. Clone the Repository  
```bash  
git clone https://github.com/tkassahu/clinical-trial-attrition-prediction.git  
cd clinical-trial-attrition-prediction  
