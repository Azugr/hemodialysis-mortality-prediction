# Hemodialysis Mortality Prediction

**Development and evaluation of machine learning models for predicting 1-year all-cause mortality in patients receiving hemodialysis using publicly available clinical data.**

## 1. Project Overview

Mortality prediction in patients receiving hemodialysis is an important challenge in clinical research. These patients frequently present with multiple comorbidities, cardiovascular complications, infections, medication burden, and complex clinical conditions.

This project aims to develop and evaluate predictive models to identify clinical, demographic, laboratory, and treatment-related factors associated with 1-year all-cause mortality in a hemodialysis-related population.

The project will use publicly available, de-identified clinical data, initially exploring the MIMIC-IV database.

## 2. Research Question

Can routinely collected demographic, clinical, laboratory, and medication-related variables predict 1-year all-cause mortality in patients receiving hemodialysis?

## 3. Research Objectives

1. Identify and extract an appropriate hemodialysis patient cohort.
2. Perform clinical data cleaning and quality assessment.
3. Explore demographic, clinical, laboratory, and medication characteristics.
4. Engineer clinically meaningful predictive features.
5. Develop and compare statistical and machine learning models.
6. Evaluate predictive performance, calibration, and interpretability.
7. Identify the most informative predictors of mortality.
8. Assess whether medication burden and treatment-related factors improve predictive performance.

## 4. Candidate Predictive Variables

Final variable selection will depend on data availability, clinical relevance, data quality, and methodological considerations.

### A. Demographic Characteristics

| Variable | Description |
|---|---|
| Age | Age at prediction date |
| Sex | Biological sex as recorded in the database |

### B. Comorbidities and Cardiovascular Conditions

| Variable | Description |
|---|---|
| Diabetes mellitus | Presence of diabetes |
| Hypertension | History of hypertension |
| Heart failure | Documented heart failure |
| Ischemic heart disease | History of coronary artery disease |
| Peripheral vascular disease | Documented peripheral vascular disease |
| Previous stroke | History of cerebrovascular disease |
| Valvular heart disease | Documented valvular disease |
| Cardiac murmur | Presence of murmur on clinical examination |
| Charlson Comorbidity Index | Summary measure of comorbidity burden |

### C. Medication Burden and Hypertension Management

| Variable | Description |
|---|---|
| Antihypertensive medication count | Number of prescribed antihypertensive agents |
| Antihypertensive polypharmacy | More than three antihypertensive medications |
| Antihypertensive medication classes | Number and types of medication classes |
| Blood pressure | Available systolic and diastolic measurements |
| Blood pressure control | Controlled, uncontrolled, or unknown, according to a predefined definition |

Antihypertensive polypharmacy will be investigated as a potential marker of cardiovascular burden and treatment complexity.

More than three medications alone does not establish resistant hypertension. Medication adherence, appropriate drug combinations, dosing, and blood pressure measurements must be considered.

### D. Infection and Clinical Complications

| Variable | Description |
|---|---|
| Previous infection | Documented infection |
| Sepsis | Documented sepsis |
| Bloodstream infection | Documented bloodstream infection |
| Infection-related hospitalization | Hospitalization associated with infection |
| ICU admission | Intensive care utilization |

### E. Laboratory and Nutritional Parameters

| Variable | Description |
|---|---|
| Albumin | Serum albumin |
| Hemoglobin | Hemoglobin concentration |
| Potassium | Serum potassium |
| Phosphorus | Serum phosphorus |
| Calcium | Serum calcium |
| Creatinine | Serum creatinine |
| WBC | White blood cell count |
| CRP | C-reactive protein, if available |
| Bicarbonate | Serum bicarbonate, if available |

### F. Hemodialysis-Related Variables

| Variable | Description |
|---|---|
| Hemodialysis status | Evidence of hemodialysis treatment |
| Dialysis vintage | Duration of dialysis treatment, if available |
| Vascular access type | Catheter, AV fistula, or AV graft |
| Access complications | Documented vascular access complications |
| Missed dialysis sessions | Missed scheduled treatments, if available |
| Dialysis adequacy | Kt/V, if available |

## 5. Primary Outcome

**One-year all-cause mortality**

- 1 = Death within 365 days after the defined prediction date.
- 0 = Confirmed survival at 365 days.
- Unknown = Insufficient follow-up or unavailable outcome information.

The prediction date, eligible population, and follow-up methodology will be established before model development.

Patients with incomplete follow-up will not automatically be classified as survivors. Censoring and competing events will be addressed where appropriate.

## 6. Dataset

**Primary candidate: MIMIC-IV**

Medical Information Mart for Intensive Care.

Source: https://physionet.org/content/mimiciv/

MIMIC-IV provides de-identified hospital clinical data, including diagnoses, laboratory measurements, medications, procedures, and mortality-related information.

Data access requires completion of applicable PhysioNet credentialing and training requirements.

The feasibility of identifying an appropriate hemodialysis cohort and obtaining sufficient longitudinal outcome information will be assessed before finalizing the study design.

## 7. Methodology and Technology Stack

### Programming and Data Engineering
- Python
- Pandas
- NumPy
- SQL

### Statistical Analysis and Machine Learning
- Scikit-learn
- Logistic Regression
- Random Forest
- Gradient Boosting

### Model Evaluation
- ROC-AUC
- Precision and Recall
- Sensitivity and Specificity
- Precision-Recall AUC
- Calibration
- Feature importance
- Model interpretability

Survival analysis methods will also be considered if the dataset and follow-up structure support time-to-event modeling.

## 8. Project Structure

```text
hemodialysis-mortality-prediction/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── synthetic/
│
├── notebooks/
│   ├── 01_exploratory_analysis.ipynb
│   ├── 02_data_quality.ipynb
│   ├── 03_feature_engineering.ipynb
│   └── 04_model_development.ipynb
│
├── src/
│   ├── data_validation.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── modeling.py
│   └── evaluation.py
│
├── tests/
├── docs/
├── reports/
├── requirements.txt
├── README.md
└── .gitignore
```

## 9. Research and Data Ethics

This project will use appropriately authorized, publicly available, de-identified datasets.

No identifiable patient information or unauthorized hospital records will be uploaded to this repository.

All analyses will comply with applicable dataset licenses, access agreements, and research requirements.

## 10. Limitations

This project is intended for research and educational purposes.

Predictive associations do not establish causation. Model performance and generalizability will depend on the source population, data quality, cohort selection, and validation strategy.

Hospital-based data may not represent the broader maintenance hemodialysis population.

The resulting models are not intended for direct clinical decision-making.

## 11. Project Status

**Status: Initial development**

Current priorities:

- Research design and cohort definition.
- Public dataset access.
- Clinical variable selection.
- Data extraction and quality assessment.
- Development of a reproducible analytical pipeline.

## 12. Author


Nephrologist | Systems Engineering | Healthcare Data & AI

Combining clinical expertise and engineering to explore data-driven approaches to healthcare research.

**Author:** Dra. María Azucena García Rodríguez
**GitHub:** [@Azugr](https://github.com/Azugr)
