# Clinical Variable Dictionary
## Hemodialysis Mortality Prediction

### 1. Purpose

This document defines the candidate clinical predictors for the development of a machine learning model to predict 1-year all-cause mortality among hospitalized adults with end-stage kidney disease (ESKD) receiving maintenance hemodialysis.

Variables are organized by clinical domain to support data identification, extraction, preprocessing, and interpretation.

**Important:** These are proposed candidate variables. Their inclusion in the final model will depend on availability, data quality, and clinical relevance in the selected public dataset.

---

### 2. Demographic Characteristics

| Variable | Description | Expected format |
|---|---|---|
| age | Patient age at index hospitalization | Numeric |
| sex | Biological sex recorded in the dataset | Categorical |

### 3. Comorbidities and Cardiovascular Risk

| Variable | Description | Expected format |
|---|---|---|
| diabetes_mellitus | History of diabetes mellitus | Binary |
| hypertension | History of hypertension | Binary |
| cardiovascular_disease | History of cardiovascular disease | Binary |
| heart_failure | History of heart failure | Binary |
| stroke_history | Previous cerebrovascular event | Binary |
| antihypertensive_polypharmacy | Use of more than three antihypertensive medications | Binary |

### 4. Dialysis and Clinical Characteristics

| Variable | Description | Expected format |
|---|---|---|
| maintenance_hemodialysis | Evidence of maintenance hemodialysis | Binary |
| dialysis_vintage | Time receiving maintenance dialysis | Numeric |
| vascular_access | Type of vascular access | Categorical |
| catheter_use | Use of a dialysis catheter | Binary |
| infection | Documented infection during index hospitalization | Binary |
| sepsis | Documented sepsis during index hospitalization | Binary |
| previous_hospitalizations | Number of previous hospitalizations | Numeric |

### 5. Nutritional Status and Protein-Energy Wasting

| Variable | Description | Expected format |
|---|---|---|
| albumin | Serum albumin concentration | Numeric |
| bmi | Body mass index | Numeric |
| creatinine | Serum creatinine concentration | Numeric |
| npcr | Normalized protein catabolic rate | Numeric |

These variables may help characterize nutritional status and protein-energy wasting. None should be interpreted independently as a definitive diagnosis of malnutrition.

### 6. Inflammation

| Variable | Description | Expected format |
|---|---|---|
| crp | C-reactive protein concentration | Numeric |
| wbc | White blood cell count | Numeric |
| neutrophils | Absolute neutrophil count | Numeric |
| lymphocytes | Absolute lymphocyte count | Numeric |
| nlr | Neutrophil-to-lymphocyte ratio | Numeric |

**Derived variable:**

NLR = Absolute neutrophil count / Absolute lymphocyte count.

This ratio may provide an additional measure of systemic inflammatory activity.

### 7. Metabolic and Electrolyte Status

| Variable | Description | Expected format |
|---|---|---|
| bicarbonate | Serum bicarbonate concentration | Numeric |
| potassium | Serum potassium concentration | Numeric |
| calcium | Serum calcium concentration | Numeric |
| phosphorus | Serum phosphorus concentration | Numeric |

Serum bicarbonate will be used to evaluate metabolic acidosis as a potential mortality predictor.

### 8. Iron Metabolism and Anemia

| Variable | Description | Expected format |
|---|---|---|
| ferritin | Serum ferritin concentration | Numeric |
| tsat | Transferrin saturation | Numeric |
| serum_iron | Serum iron concentration | Numeric |
| tibc | Total iron-binding capacity | Numeric |
| transferrin | Serum transferrin concentration | Numeric |
| hemoglobin | Hemoglobin concentration | Numeric |
| iv_iron_exposure | Intravenous iron administration | Numeric |
| esa_exposure | Erythropoiesis-stimulating agent exposure | Numeric |

**Clinical considerations:**

- Elevated ferritin does not necessarily indicate iron overload.
- Ferritin must be interpreted alongside inflammatory markers.
- TSAT provides additional information about circulating iron availability.
- Cumulative intravenous iron exposure may be useful when longitudinal treatment data are available.
- MRI-based liver iron concentration would be a more direct measure of tissue iron accumulation, if available.

### 9. Outcome Variable

| Variable | Description | Expected format |
|---|---|---|
| mortality_365d | All-cause mortality within 365 days after hospital discharge | Binary |

Coding:

- 1 = Death within 365 days.
- 0 = No documented death within 365 days, with adequate follow-up.

Patients without sufficient follow-up must not automatically be classified as survivors.

### 10. Data Quality and Preprocessing

For each candidate variable, we will document:

- Original dataset column name.
- Measurement unit.
- Missing-value percentage.
- Number of available observations.
- Measurement date relative to hospital discharge.
- Outliers and implausible values.
- Preprocessing method.
- Final inclusion or exclusion decision.

### 11. Prediction Time and Data Leakage Prevention

The prediction time is defined as hospital discharge.

Only information available on or before discharge may be used as a predictor.

Laboratory measurements will be selected using a predefined time window before discharge.

Post-discharge information must not be used as a predictor.

### 12. Variable Selection Strategy

Candidate variables will be evaluated according to:

1. Clinical relevance.
2. Availability in the selected dataset.
3. Data completeness.
4. Measurement reliability.
5. Potential predictive contribution.
6. Risk of data leakage.

The final feature set will be documented and justified.

---

**Author:** Dra. María Azucena García Rodríguez
**GitHub:** [@Azugr](https://github.com/Azugr)

**Project:** Hemodialysis Mortality Prediction

**Status:** Preliminary clinical variable specification.
