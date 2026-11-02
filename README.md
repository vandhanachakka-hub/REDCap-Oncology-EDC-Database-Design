# Phase II Oncology Clinical Trial Database Design & Architecture (REDCap)

## 📌 Project Overview
This portfolio project showcases a fully compliant, multi-instrument electronic data capture (EDC) system designed from scratch utilizing the *REDCap* platform. The database simulates a multi-center Phase II clinical trial evaluating an investigational targeted therapy for patients with advanced Non-Small Cell Lung Cancer (NSCLC). 

The repository demonstrates hands-on technical competencies required for entry-level *Clinical Data Management (CDM)* roles, specifically focusing on data integrity, point-of-entry data cleaning, clinical coding, and protocol timeline adherence.

---

## 🛠️ Data Management Core Implementations

### 1. eCRF Development & Data Standards Alignment
*   *Demographics & Screening (DM):* Configured standard electronic Case Report Forms capturing patient informed consent dates, age parameters, and trial eligibility indicators using systematic naming conventions.
*   *Adverse Event (AE) Report:* Developed an interactive safety instrument aligned with *CDASH / SDTM* domains to track ongoing medical developments during the study lifecycle.

### 2. Point-of-Entry Data Validation & Range Checks
*   *Age Restraints:* Programmed hard integer ceiling and floor boundaries (18–85) within the database to instantly flag ineligible pediatric or geriatric patient entries at the point of transcription.
*   *Format Constraints:* Enforced system-wide standardization for numeric entries and date fields (YYYY-MM-DD) to minimize data variations.

### 3. Advanced Conditional Logic & Interactive Architecture
*   *Branching Logic:* Implemented dynamic expressions ([eligibility_check] = '0') to automatically reveal conditional clinical notes fields only when a patient fails protocol eligibility, reducing user fatigue for coordinators.
*   *Action Tags:* Deployed system-level action tags (@NOTICE-WARNING) to display bright regulatory warning alerts on screen whenever an entry is declared a Serious Adverse Event (SAE).

### 4. Relational Repeating Instruments
*   Configured independent *Repeating Instruments* for the Adverse Event log. This architectural configuration allows multiple separate safety entries to be filed over time against a single, longitudinal patient record without structural duplication.

### 5. Programmatic Edit Checks & Query Simulation
*   Scripted and executed automated Data Quality rules using logic constraints to detect impossible chronological anomalies across datasets:
    text
    [ae_onset_date] < [ic_date]
    
*   This specific check scans the database to isolate cases where an Adverse Event onset date accidentally precedes the signature date of Informed Consent, simulating the data query generation process.

### 6. Clinical Medical Coding (MedDRA)
*   Utilized the hierarchical *MedDRA dictionary* to execute clinical coding workflows. Handled the normalization of verbatim, free-text adverse event entries submitted on eCRFs down to their standardized *Preferred Terms (PT)* and *System Organ Classes (SOC)*.

---

## 📂 Repository Artifacts
*   *[Click to View Demographics eCRF Layout PDF](file:///C:/Users/DELL/Downloads/Demographics_OncologyNSCLCPhas%20(1).pdf)* - Full visual output of the screening form constraints.
*   *[Click to View Adverse Event eCRF Layout PDF](file:///C:/Users/DELL/Downloads/AdverseEvent_OncologyNSCLCPhas%20(1).pdf)* - Visual output of the safety reporting layout.
*   *[Click to View Data Dictionary CSV]()* - The underlying structural metadata layout mapping all fields, data choices, branching logic, and variables.
