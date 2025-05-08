# Association of Patient's Preferred Language on Sedation Practices During Mechanical Ventilation.
## Objective
* Primary: Elucidate the association between EHR documented patient preferred language and rates of deep sedation in the first 48-hours of mechanical ventilation 
* Secondary: Determine the association between EHR documented patient preferred language and known long-term complications of early deep sedation

## Required CLIF Tables and fields
Please refer to the online CLIF data dictionary, ETL tools, and specific table contacts for more information on constructing the required tables and fields. List all required tables for the project here, and provide a brief rationale for why they are required.

### To build cohort
* `patient_assessments`
    - `hospitalization_id`, `recorded_dttm`, `numerical_value`, `categorical_value`
    - `assessment_category %in% c("RASS", "gcs_total", "sbt_screen_pass_fail")`
* `vitals`
    - `hospitalization_id`, `recorded_dttm`, `vital_value`
    - `vital_catgories %in% c("height_cm", "weight_kg", "sbp", "dbp", "map", "spo2")`
* `labs`
    - `hospitalization_id`, `lab_collect_dttm`, `lab_value_numeric`
    - `lab_category %in% c("creatinine", "bilirubin_total", "platelet_count", "po2_arterial", "pco2_arterial", "ph_arterial")`
* `medication_admin_continuous`
    - `hospitalization_id`, `admin_dttm`, `med_dose`, `med_dose_unit`
    - `med_category %in% c("norepinephrine", "vasopressin", "epinephrine", "phenylephrine", "cisatracurium", "milrinone", "vecuronium", "dobutamine", "dopamine", "rocuronium", "isoproterenol")`
* `ADT`
    - `hospitalization_id`, `hospital_id`, `in_dttm`, `out_dttm`, `location_category`, `location_type`
* `hospitalization`
    - `patient_id`, `hospitalization_id`, `age_at_admission`, `admission_dttm`, `discharge_dttm`, `admission_type_category`, `discharge_category`
* `patient`
    - Need complete table including: `patient_id`, `language_name`, `death_dttm`, `race_category`, `sex_category`, `ethnicity_category`
* `respiratory_support`
    - `hospitalization_id`, `recorded_dttm`, `device_category`, `mode_category`, `tracheostomy`, `fio2_set`, `peep_set`, `lpm_set`, `tidal_volume_set`
    - `device_category %in% c("IMV", "Trach Collar")`
 
## Cohort Identification
Adults with documented IMV periods >24 hours. There are no date constraints.

## Expected Results
* Two Cohort Language Summary (html file)
* Two Data Cleaning Summaries (csv files)
* Two ATS Data Analysis Files (csv files)
* Primary Analysis (csv file)
* Ten Sensitivity Analyses (csv files)
* Eight Secondary Analyses (csv files)
* Two Sub-Group Analyses (csv files)

## Detailed Instructions
1. Update yaml file in config folder with base directory, location to store project files, file type, and institution
2. In Rstudio, Set Working Directory to "CLIF_Deep_Sedation_Language/config"
3. Run [CODE](https://github.com/acortizmd/CLIF_Deep_Sedation_Language/tree/main/code) starting with 00_cohort_id
4. Deposit results:

Please deposit your "final_data" folder in this [box folder](https://uchicago.app.box.com/s/1g90ydgtwkkewrmgsowd98j1ys4mpgk4)
