# Healthcare Data Analysis and Patient Insights

**IBM SkillsBuild Data Analytics with AI Internship 2026**
**Student:** Atreyee Ghorai

---

## Project Overview

This project analyzes a **synthetic healthcare dataset** to identify meaningful patterns related to patient demographics, symptoms, department workloads, vital signs, symptom severity, and chronic conditions.

The raw CSV contains **150,500 rows**, including 500 duplicate records. After data cleaning and duplicate removal, **150,000 records** remain for analysis.

The project follows a complete data analytics workflow — from raw data loading and cleaning through exploratory data analysis, calculations, grouping, visualization, healthcare-focused questions, key insights, business decisions, and an exploratory AI/ML evaluation.

> **Disclaimer:** The dataset is synthetic healthcare data generated for educational and data analytics purposes. It does not represent real patient records and must not be used for medical diagnosis, treatment, or clinical decision-making.

---

## Problem Statement

Healthcare organizations generate large amounts of patient information. Analyzing this information can help identify patterns in patient demographics, symptoms, department workloads, vital signs, and healthcare service requirements.

This project demonstrates how data analytics techniques can be used to clean healthcare data, explore patient patterns, visualize important findings, answer practical healthcare-related questions, and investigate whether basic patient characteristics and vital signs provide useful predictive signals.

---
## Dataset: [Healthcare Raw Dataset – Google Drive](https://drive.google.com/file/d/1RpqomOGwRL87BPNIBPInLq2jUIA70wNm/view?usp=sharing)

## Dataset

| Attribute         | Value                                              |
| ----------------- | -------------------------------------------------- |
| File              | `data/healthcare_raw_data_150000.csv`              |
| Raw Records       | 150,500                                            |
| Duplicate Records | 500                                                |
| Cleaned Records   | 150,000                                            |
| Columns           | 14                                                 |
| Data Type         | Synthetic healthcare data for educational purposes |

### Dataset Columns

The dataset contains the following 14 columns:

`patient_id`, `age`, `gender`, `symptoms`, `temperature`, `duration_days`, `bp_systolic`, `bp_diastolic`, `heart_rate`, `oxygen_saturation`, `pain_level`, `symptom_severity`, `chronic_condition`, `department`

---

## Project Structure

```text
Healthcare-Data-Analysis/
│
├── data/
│   └── healthcare_raw_data_150000.csv
│
├── notebooks/
│   └── AtreyeeGhorai_Healthcare_Data_Analysis_and_Patient_Insights.ipynb
│
├── scripts/
│   └── Analysis and notebook-generation scripts
│
├── outputs/
│   └── charts/
│
├── requirements.txt
└── README.md
```

> The raw dataset is preserved separately from the cleaned analysis data.

---

## Notebook Sections

The notebook follows these major sections:

1. Project Overview
2. Problem Statement
3. Objectives
4. Dataset Information
5. Import Libraries
6. Load Dataset
7. Data Understanding
8. Data Cleaning
9. Exploratory Data Analysis
10. Data Calculations
11. Data Grouping and Aggregation
12. Data Visualizations
13. Live Analysis — 10 Key Questions
14. Key Insights
15. Healthcare & Business Decisions
16. AI / Machine Learning
17. Model Evaluation
18. AI / ML Insights
19. Limitations
20. Future Scope
21. Conclusion

---

## Key Findings

The following findings were calculated from the cleaned dataset:

| Finding                                     |                        Result |
| ------------------------------------------- | ----------------------------: |
| Average patient age                         |                   49.05 years |
| Most common symptom                         |   Chest Pain — 6,629 patients |
| Busiest department                          | Dermatology — 24,447 patients |
| Most common severity                        |                  Mild — 45.3% |
| Chronic condition prevalence                |                        37.28% |
| Highest average heart rate department       |        Cardiology — 87.59 bpm |
| Highest average pain department             |         Orthopedics — 6.90/10 |
| Lowest average oxygen saturation department |          Pulmonology — 96.25% |
| Largest age group                           | 61–80 years — 47,402 patients |

These findings describe patterns in the synthetic dataset and should not be interpreted as representative of real patient populations.

---

## Data Cleaning

The raw dataset contained several data-quality issues that were addressed during preprocessing, including:

* Duplicate records
* Missing values
* Inconsistent categorical values
* Invalid or unusual oxygen-saturation values
* Extreme blood-pressure observations
* Data-type consistency issues

The cleaning process was performed while preserving the original raw dataset.

After cleaning and duplicate removal:

* **Raw rows:** 150,500
* **Final analysis rows:** 150,000

The notebook documents the cleaning decisions and their impact on the dataset.

---

## Exploratory Data Analysis

The project explores:

* Patient age distribution
* Gender distribution
* Common symptoms
* Department workload
* Symptom severity
* Chronic-condition prevalence
* Vital-sign distributions
* Department-wise vital-sign patterns
* Relationships between numerical variables
* Patient age groups

Visualizations include appropriate bar charts, count plots, histograms, box plots, and correlation analysis.

---

## Live Analysis — Key Questions

The notebook answers practical questions based on the actual dataset, including questions related to:

* Patient demographics
* Common symptoms
* Department workloads
* Symptom severity
* Chronic conditions
* Age groups
* Department-wise vital signs
* Pain levels
* Oxygen saturation
* Operational healthcare patterns

Each question is supported by a calculated answer and a corresponding insight.

---

# Machine Learning

## ML Objective

The exploratory ML task investigates whether basic patient demographics, vital signs, and symptom-related severity information can provide useful predictive signals for **department assignment**.

### Target

`department`

The target contains **9 department classes**.

### Features

The model uses:

* `age`
* `temperature`
* `duration_days`
* `bp_systolic`
* `bp_diastolic`
* `heart_rate`
* `oxygen_saturation`
* `pain_level`
* `gender`
* `chronic_condition`
* `symptom_severity`

The `symptoms` feature was deliberately excluded.

---

## Why `symptoms` Was Excluded

During ML investigation, a strong relationship was found between `symptoms` and `department` in this synthetic dataset.

A simple symptom-to-department lookup achieved approximately **95.6% accuracy**, while a Decision Tree using the symptom encoding achieved approximately **95.35% accuracy**.

This indicates that the synthetic dataset contains a near-deterministic relationship between symptoms and department assignment.

Including `symptoms` would therefore allow the model to largely reproduce the synthetic assignment rule rather than demonstrate meaningful learning from independent patient characteristics.

For this reason, `symptoms` was excluded from the final ML experiment.

> This finding is a limitation of the synthetic dataset and should not be interpreted as evidence that symptoms determine hospital departments in real-world healthcare.

---

## Final ML Model

**Model:** Decision Tree Classifier

**Target:** `department`

**Features:** Vital signs, demographics, duration, pain level, chronic-condition information, and symptom severity

**Accuracy:** **16.83%**

### Baselines

| Baseline                | Accuracy |
| ----------------------- | -------: |
| Uniform random baseline |    11.1% |
| Majority-class baseline |    16.3% |
| Decision Tree           |   16.83% |

The Decision Tree performs only slightly above the majority-class baseline.

This indicates that the available vital-sign and demographic features provide **limited predictive signal for department assignment in this synthetic dataset**.

The result is not presented as a clinical prediction system.

---

## Why `symptom_severity` Was Not Used as the Target

`symptom_severity` was also investigated as a possible ML target.

A model targeting symptom severity achieved approximately **27% accuracy**, while the majority-class baseline was approximately **45.3%**.

Therefore, the available features did not provide sufficient predictive value for this target in the synthetic dataset.

The project consequently uses `department` as the ML target while excluding the highly department-associated `symptoms` feature.

---

## ML Interpretation

The ML experiment demonstrates an important data analytics lesson:

**A high model accuracy does not automatically mean that a model has learned a meaningful real-world relationship.**

The initial high-performing symptom-based model was investigated and found to be largely reproducing a relationship already embedded in the synthetic data.

After excluding that feature, the model achieved 16.83% accuracy, showing that the remaining features have limited predictive signal for department assignment.

This emphasizes the importance of:

* Feature investigation
* Target selection
* Baseline comparison
* Leakage-like relationship detection
* Honest model evaluation
* Understanding the data-generation process

---

## Healthcare & Business Decisions

Based on the descriptive analysis of the synthetic dataset, potential operational considerations include:

### Resource Planning

Department-level patient volumes can help demonstrate how healthcare organizations might plan staffing and operational resources.

### Staff Allocation

Differences in patient volume, pain levels, and vital-sign distributions can support exploratory workload analysis.

### Patient Service Improvement

Understanding common symptoms and patient demographics can help identify areas for improving patient-facing services.

### Operational Monitoring

Regular analysis of department workloads and patient characteristics can help organizations monitor changing patterns over time when appropriate data is available.

> These are analytical and operational considerations, not clinical recommendations or medical advice.

---

## Limitations

This project has several important limitations:

* The dataset is **synthetic** and does not represent a real clinical population.
* The data-generation process creates strong relationships between some variables.
* The symptom-to-department relationship is unusually strong because of the synthetic data-generation process.
* The final ML model has limited predictive performance using the selected features.
* The 16.83% ML result should not be interpreted as real-world clinical predictive performance.
* Missing values were handled through preprocessing techniques such as median/mode imputation where appropriate.
* The raw dataset contains intentionally introduced data-quality issues for educational analysis.
* No temporal information is available for longitudinal trend analysis.
* The dataset does not contain information such as treatment cost, hospital stay duration, admission type, or treatment outcomes.
* The analysis cannot be used for diagnosis, treatment recommendations, or clinical decision-making.

---

## Future Scope

Future versions of the project could include:

* Larger and properly anonymized real-world healthcare datasets
* Temporal patient records
* Hospital admission and discharge information
* Treatment outcomes
* Hospital stay duration
* Healthcare cost analysis
* More comprehensive feature engineering
* Advanced ML model comparison
* Model explainability techniques
* Model monitoring and validation on independent datasets
* Interactive dashboards using tools such as Tableau or Power BI

Any real-world healthcare ML application would require appropriate clinical validation, privacy protections, governance, and domain expertise.

---

## How to Run

### 1. Clone or Download the Repository

```bash
git clone <repository-url>

cd Healthcare-Data-Analysis
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook notebooks/TanishqBanger_Healthcare_Data_Analysis_and_Patient_Insights.ipynb
```

### 4. Run All Cells

Use:

**Kernel → Restart & Run All**

to execute the complete notebook from beginning to end.

---

## Deliverables

| File                                                                             | Description                        |
| -------------------------------------------------------------------------------- | ---------------------------------- |
| `notebooks/AtreyeeGhorai_Healthcare_Data_Analysis_and_Patient_Insights.ipynb`    | Main data analysis and ML notebook |
| `AtreyeeGhorai_Healthcare_Data_Analysis_and_Patient_Insights_ProjectReport.docx` | Project report                     |
| `requirements.txt`                                                               | Python dependencies                |
| `README.md`                                                                      | Project documentation              |

---

## Libraries Used

| Library        | Purpose                                           |
| -------------- | ------------------------------------------------- |
| `pandas`       | Data loading, cleaning, analysis, and aggregation |
| `numpy`        | Numerical operations                              |
| `matplotlib`   | Data visualization                                |
| `seaborn`      | Statistical visualization                         |
| `scikit-learn` | Machine learning and model evaluation             |
| `nbformat`     | Notebook processing and validation                |
| `jupyter`      | Running the analysis notebook                     |

---

## Conclusion

This project demonstrates an end-to-end healthcare data analytics workflow using a synthetic dataset.

The analysis identifies patterns in patient demographics, symptoms, department workloads, vital signs, symptom severity, and chronic conditions. It also demonstrates the importance of data cleaning, exploratory analysis, visualization, baseline comparison, and careful interpretation of machine-learning results.

The ML investigation was particularly important because the synthetic dataset contained a strong symptom-to-department relationship. Investigating this relationship prevented the project from presenting an artificially high model accuracy as meaningful predictive performance.

The final ML experiment, using vital signs and demographic features without `symptoms`, achieved **16.83% accuracy**, which is only slightly above the **16.3% majority-class baseline**. This demonstrates that the selected features provide limited predictive signal for department assignment within this synthetic dataset.

Overall, the project demonstrates that effective data analytics is not only about obtaining high model accuracy, but also about understanding the data, validating assumptions, identifying limitations, and communicating findings honestly.

---

**IBM SkillsBuild Data Analytics with AI Internship 2026**
**Student: Atreyee Ghorai**
