# Hemodialysis Mortality Prediction

## Project Overview

This project aims to develop and evaluate machine learning models to predict 1-year all-cause mortality among hospitalized adults with end-stage kidney disease (ESKD) receiving hemodialysis.

The model will use clinical, laboratory, nutritional, inflammatory, metabolic, and treatment-related variables available in publicly accessible clinical datasets.

The prediction will be made at hospital discharge, with mortality assessed during the subsequent 365 days.

The primary objective is to identify clinically relevant predictors of mortality and evaluate whether machine learning approaches can improve risk stratification in this population.

## Research Objectives

- Develop predictive models for 1-year all-cause mortality.
- Identify relevant clinical and laboratory predictors.
- Evaluate the contribution of nutritional status, chronic inflammation, and metabolic abnormalities.
- Investigate the relationship between iron metabolism and mortality risk.
- Compare machine learning algorithms with traditional logistic regression.
- Evaluate model discrimination, calibration, and clinical usefulness.

## Candidate Predictors

Variables will be organized into the following clinical domains.

### 1. Demographic Characteristics
- Age
- Sex

### 2. Comorbidities and Cardiovascular Risk
- Diabetes mellitus
- Hypertension
- Cardiovascular disease
- Heart failure
- History of stroke
- Antihypertensive polypharmacy (more than three medications)

### 3. Dialysis and Clinical Characteristics
- Hemodialysis dependence
- Dialysis-related characteristics, when available
- Vascular access type
- Catheter use
- Hospitalization history
- Infection and sepsis

### 4. Nutritional Status and Protein-Energy Wasting
- Serum albumin
- Body mass index (BMI)
- Serum creatinine
- Normalized protein catabolic rate (nPCR), when available
- Nutritional indicators, when available

### 5. Inflammation
- C-reactive protein (CRP)
- White blood cell count
- Neutrophil count
- Lymphocyte count
- Neutrophil-to-lymphocyte ratio (NLR)

### 6. Metabolic and Electrolyte Status
- Serum bicarbonate
- Potassium
- Calcium
- Phosphorus
- Other available metabolic parameters

Metabolic acidosis will be evaluated using serum bicarbonate as a candidate predictor.

### 7. Iron Metabolism and Anemia
- Ferritin
- Transferrin saturation (TSAT)
- Serum iron
- Transferrin or total iron-binding capacity (TIBC)
- Hemoglobin
- Intravenous iron exposure, when available
- Erythropoiesis-stimulating agent (ESA) exposure, when available

Ferritin will be interpreted alongside inflammatory markers because elevated ferritin does not necessarily indicate iron overload.

## Outcome

**Primary outcome:** All-cause mortality within 365 days after hospital discharge.

## Data Sources

The initial development will use publicly available, de-identified clinical data.

Potential sources include:

- MIMIC-IV
- Other publicly accessible clinical datasets with relevant dialysis and mortality information.

Dataset selection will depend on the availability of hemodialysis-specific clinical variables, follow-up information, and outcome definitions.

No identifiable patient information or private clinical records will be uploaded to this repository.

## Methodology

The planned workflow includes:

1. Data acquisition and cohort definition.
2. Data cleaning and preprocessing.
3. Exploratory data analysis.
4. Missing-data assessment and management.
5. Feature engineering and selection.
6. Logistic regression as a baseline model.
7. Machine learning model development.
8. Model evaluation and comparison.
9. Interpretation of clinically relevant predictors.

Evaluation metrics will include:

- AUROC
- AUPRC
- Sensitivity
- Specificity
- Positive predictive value
- Calibration

## Research Considerations

- Association does not establish causation.
- Elevated ferritin alone will not be considered proof of iron overload.
- Nutritional and inflammatory markers will be evaluated as distinct but potentially overlapping clinical domains.
- Missing clinical variables will be documented and assessed.
- Data leakage will be avoided by ensuring that predictors are available at the defined prediction time.
- Model performance and generalizability will be evaluated critically.

## Technology Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

Additional libraries may be incorporated as the project develops.

## Project Status

<text>In development.</text>

The current phase focuses on defining the study population, identifying suitable public datasets, and establishing the clinical and methodological framework.

## 12. Author

Nephrologist | Systems Engineering | Healthcare Data & AI

Combining clinical expertise and engineering to explore data-driven approaches to healthcare research.

**Author:** Dra. María Azucena García Rodríguez
**GitHub:** [@Azugr](https://github.com/Azugr)

## License

MIT License

---

**Disclaimer:** This project is intended for research and educational purposes. It is not designed to replace clinical judgment or provide individual patient treatment recommendations.

