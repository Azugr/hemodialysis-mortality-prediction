# Clinical Variable Dictionary
## Hemodialysis Mortality Prediction
### CMS ESRD Population Public Use Files (PUF)

**Version:** 2.0 – CMS dataset adaptation  
**Status:** Preliminary; pending validation of outcome and follow-up dates.

### 1. Purpose

This document defines the candidate clinical predictors, demographic characteristics, dialysis-related variables, and outcome measures for a clinical data science project investigating mortality among patients receiving maintenance hemodialysis.

The current data source is the CMS End-Stage Renal Disease (ESRD) Population Public Use File (PUF), 2018 Q4 release.

The initial research question is:

**Can routinely collected demographic, clinical, laboratory, and dialysis-related variables predict mortality among patients receiving maintenance hemodialysis?**

The original objective of predicting 1-year all-cause mortality remains under evaluation. Its feasibility depends on validating the available dates, follow-up periods, and mortality records.

**Important:** Candidate variables are not necessarily available in the currently downloaded files. Their final inclusion will depend on actual data availability, completeness, measurement timing, and clinical relevance.

### 2. Study Population and Prediction Time

**Target population:** Adults with evidence of maintenance hemodialysis treatment.

The CMS PUF contains a broader ESRD population, including different dialysis modalities and transplantation. The maintenance hemodialysis cohort must therefore be identified using treatment-history records.

**Prediction time:** Not yet finalized.

The original hospital-discharge prediction point cannot be assumed to apply to this dataset. A suitable index date must be established from the available treatment and clinical records.

Only information available at or before the selected index date may be used as a predictor.

### 3. Demographic Characteristics

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| age_range | PATIENT_SUMMARY: AGE_RANGE | Available as age categories, not exact age |
| sex | PATIENT_SUMMARY: GENDER | Available |
| race | PATIENT_SUMMARY: RACE | Available |
| ethnicity | PATIENT_SUMMARY: ETHNICITY | Available, with substantial missingness |
| state | PATIENT_SUMMARY: STATE | Available |

Age categories must not be treated as exact ages without an explicitly documented approximation strategy.

### 4. Comorbidities and Cardiovascular Risk

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| diabetes_mellitus | FORM_2728 | Available through reported comorbidity fields; form versions differ |
| hypertension | FORM_2728 | Available |
| cardiovascular_disease | FORM_2728 | Requires a documented definition using specific cardiac fields |
| heart_failure | FORM_2728 | Available |
| stroke_history | FORM_2728 | Available through cerebrovascular history fields |
| peripheral_vascular_disease | FORM_2728 | Available |
| coronary_artery_disease | FORM_2728 | Mapping depends on form version |
| antihypertensive_polypharmacy | Not established | More than three medications cannot be derived from the currently documented variables |

Comorbidities must be harmonized across the 1997, 2005, and 2015 versions of Form CMS-2728.

A missing comorbidity field must not automatically be interpreted as absence of disease.

Antihypertensive polypharmacy must not be included unless medication-level information becomes available.

### 5. Dialysis and Treatment Characteristics

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| maintenance_hemodialysis | ADMIT_TREATMENT: Dialysis_Type, Modality | Available; requires treatment-history reconstruction |
| dialysis_setting | ADMIT_TREATMENT: Dialysis_Setting | Available |
| dialysis_vintage | PATIENT_SUMMARY: DOFD; treatment records | Limited by date precision and reference-date validation |
| sessions_per_week | ADMIT_TREATMENT: Sessions_per_Week | Available where recorded |
| vascular_access | CL_HD_VA | Documented in the data dictionary; file not yet analyzed |
| catheter_use | CL_HD_VA | Requires access-type classification |
| infection | CL_HD_INFECTION | Includes infections requiring hospitalization |
| infection_type | CL_HD_INFECTION | Includes access-related and non-access-related infection categories |
| previous_hospitalizations | CL_HOSPITALIZATION | Requires longitudinal event reconstruction |
| hospitalization_diagnosis | CL_HOSPITALIZATION | Includes cardiovascular, infectious, respiratory, and other diagnoses |
| delivered_kt_v | CL_HD_ADQCY | Documented in the data dictionary; file not yet analyzed |
| residual_renal_function | CL_HD_ADQCY | Documented in the data dictionary; file not yet analyzed |

Treatment records are not independent patient observations. Multiple facilities and treatment episodes may exist for the same patient.

Patient-level analyses must account for repeated records.

### 6. Nutritional Status and Protein-Energy Wasting

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| albumin | CL_MINERALMET | Documented in the data dictionary |
| creatinine | Not yet confirmed | Requires verification in available files |
| npcr | CL_HD_ADQCY | Documented in the data dictionary |
| bmi | Not yet confirmed | Requires verification |

These variables may help characterize nutritional status and protein-energy wasting. None should be interpreted independently as a definitive diagnosis of malnutrition.

### 7. Inflammation

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| crp | Not yet confirmed | Requires verification |
| wbc | Not yet confirmed | Requires verification |
| neutrophils | Not yet confirmed | Requires verification |
| lymphocytes | Not yet confirmed | Requires verification |
| nlr | Derived variable | Requires absolute neutrophil and lymphocyte counts |

**Derived variable:**

NLR = Absolute neutrophil count / Absolute lymphocyte count.

This variable will only be calculated if both measurements are available and sufficiently reliable.

### 8. Metabolic and Mineral Status

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| phosphorus | CL_MINERALMET | Documented |
| calcium | CL_MINERALMET | Documented; corrected and uncorrected values must be distinguished |
| potassium | Not yet confirmed | Requires verification |
| bicarbonate | Not yet confirmed | Requires verification |
| parathyroid_hormone | Not yet confirmed | Requires verification |

Serum bicarbonate, if available, may be used to investigate metabolic acidosis as a potential predictor.

### 9. Iron Metabolism and Anemia

| Analytical variable | CMS source | Availability / limitation |
|---|---|---|
| hemoglobin | CL_ANEMIA_MGT | Documented |
| ferritin | CL_ANEMIA_MGT | Documented |
| tsat | CL_ANEMIA_MGT | Documented |
| iv_iron_exposure | CL_ANEMIA_MGT / related treatment data | Requires verification of exposure fields |
| esa_exposure | CL_ANEMIA_MGT | Requires verification of treatment fields |
| serum_iron | Not yet confirmed | Requires verification |
| tibc | Not yet confirmed | Requires verification |
| transferrin | Not yet confirmed | Requires verification |

**Clinical considerations:**

- Elevated ferritin does not necessarily indicate iron overload.
- Ferritin must be interpreted alongside inflammatory markers
