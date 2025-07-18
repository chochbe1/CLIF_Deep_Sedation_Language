# Association of Patient's Preferred Language on Sedation Practices During Mechanical Ventilation.
## Objective
* Primary: Elucidate the association between EHR documented patient preferred language and rates of deep sedation in the first 48-hours of mechanical ventilation 
* Secondary: Determine the association between EHR documented patient preferred language and known long-term complications of early deep sedation

## Required CLIF Tables and fields
Please refer to the online CLIF data dictionary, ETL tools, and specific table contacts for more information on constructing the required tables and fields. List all required tables for the project here, and provide a brief rationale for why they are required.

### To build cohort
* `patient_assessments`
    - `hospitalization_id`, `recorded_dttm`, `numerical_value`, `categorical_value`
    - `assessment_category %in% c("RASS", "gcs_total")`
* `vitals`
    - `hospitalization_id`, `recorded_dttm`, `vital_value`
    - `vital_catgories %in% c("height_cm", "weight_kg", "sbp", "dbp", "map", "spo2", "temp_c", "heart_rate", "respiratory_rate")`
* `labs`
    - `hospitalization_id`, `lab_collect_dttm`, `lab_value_numeric`, `lab_order_dttm`, `lab_category`, `lab_result_dttm`
    - `lab_category %in% c("creatinine", "bilirubin_total", "platelet_count", "po2_arterial", "pco2_arterial", "ph_arterial", "anion_gap", "troponin_t", "troponin_i", "sodium", "bicarbonate", "chloride", "bun", "albumin", "glucose_serum", "hemoglobin", "hematocrit", "lactate", "so2_arterial", "wbc")`
* `medication_admin_continuous`
    - `hospitalization_id`, `admin_dttm`, `med_dose`, `med_dose_unit`, `med_category`, `med_group`
    - `med_group %in% c("vasoactives", "sedation", "paralytics")`
* `ADT`
    - `hospitalization_id`, `hospital_id`, `in_dttm`, `out_dttm`, `location_category`, `location_type`
* `hospitalization`
    - `patient_id`, `hospitalization_id`, `age_at_admission`, `admission_dttm`, `discharge_dttm`, `admission_type_category`, `zipcode_five_digit`, `discharge_category`
* `patient`
    - Need: `patient_id`, `language_category`, `death_dttm`, `race_category`, `sex_category`, `ethnicity_category`
* `respiratory_support`
    - `hospitalization_id`, `recorded_dttm`, `device_category`, `mode_category`, `tracheostomy`, `fio2_set`, `peep_set`, `lpm_set`, `tidal_volume_set`
    - `device_category %in% c("IMV", "Trach Collar")`
* `hospital_diagnosis` 
    - `hospitalization_id`, `diagnostic_code`, `diagnosis_code_format`
    - Will only work with ICD-10 codes
* `medication_admin_intermittent`
    - `hospitalization_id`, `admin_dttm`, `med_dose`, `med_group`, `med_category`
    - `med_group %in% c("paralytics")`
* `microbiology_nonculture`
    - `patient_id`, `hospitalization_id` `result_dttm`, `result_category`
 
## Cohort Identification
Adults with documented IMV periods >24 hours. There are no date constraints.

## Expected Results - Please upload the following to Box
* final_data folder - 33 total files - 2 data cleaning summaries, 2 LAPS2 missing summaries, 1 language count, 1 histogram, 1 primary analysis, 1 kappa table, 13 sensitivity analyses, 9 secondary analyses, 3 subgroup analyses
* final_tables folder - 13 total files
* secondary_project folder - 63 files

## Detailed Instructions
1. Update yaml file in config folder with base directory, location to store project files, file type, and institution
2. In Rstudio, Set Working Directory to "CLIF_Deep_Sedation_Language/config"
3. Run [CODE](https://github.com/acortizmd/CLIF_Deep_Sedation_Language/tree/main/code) starting with 00_cohort_id
4. Deposit results:

Please deposit your "final_data" folder in this [box folder]([https://uchicago.app.box.com/s/1g90ydgtwkkewrmgsowd98j1ys4mpgk4](https://app.box.com/folder/291920680241))
