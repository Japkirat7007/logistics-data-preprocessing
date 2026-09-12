# Logistics Data Preprocessing

This project was completed as part of my Logistics Data Analyst Internship at Yuva Intern. It demonstrates a structured and reproducible data preprocessing workflow using a real-world public logistics dataset.

## Project Objective

The objective of this project is to prepare logistics data for further analysis by identifying data-quality issues, handling missing information, validating data types, detecting potential outliers, and normalizing selected quantitative features using Python.

## Dataset

The project uses the **Cargo 2000 Freight Tracking and Tracing** dataset from the UCI Machine Learning Repository.

- Raw CSV: 3,943 rows and 98 variables
- Valid process records after removing one completely empty row: 3,942
- Dataset domain: air-freight tracking and tracing
- Data type: multivariate and sequential logistics event data

## Key Preprocessing Results

- Identified 210,186 non-standard `?` missing-value placeholders across 72 variables.
- Removed one completely empty record.
- Removed 30 variables with at least 90% missingness using a project-specific conservative threshold.
- Retained 68 original variables after sparse-column removal.
- Converted 44 planned and effective duration features to numeric format.
- Detected potential duration outliers using the IQR method.
- Retained IQR-flagged observations rather than automatically deleting potentially genuine logistics delays.
- Confirmed that the analyzed duration variables contained no negative or zero values.
- Applied Min-Max normalization to 16 complete quantitative duration features.
- Preserved the original duration values in minutes.
- Final processed dataset: 3,942 rows and 84 variables.

## Tools and Technologies

Python, pandas, NumPy, Matplotlib, scikit-learn, Google Colab, and GitHub.

## Repository Files

- `Yuva_Intern_Task_2_Logistics_Data_Preprocessing.ipynb` – complete Python preprocessing notebook
- `Task_2_Processed_Logistics_Dataset.csv` – final processed logistics dataset
- `Task_2_Research_Sources.txt` – research sources and preprocessing principles
- `Task_2_Missing_Value_Detection.png` – missing-value detection visualization
- `Task_2_IQR_Outlier_Percentage.png` – IQR outlier analysis visualization
- `Task_2_Normalization_Comparison.png` – normalization comparison visualization

## Methodology

The preprocessing decisions followed a problem → detection → treatment → justification → effect approach. Missing information was investigated before treatment, variable meaning was checked before numeric conversion, and potential statistical outliers were not automatically treated as errors without operational evidence.

Numeric-looking identifiers such as process IDs, transport-leg IDs, and masked airport identifiers were not treated as continuous measurements. Normalization was limited to meaningful quantitative duration features.

## Data Quality and Limitations

The final dataset intentionally retains missing values in 42 variables. These values were not filled through indiscriminate imputation because doing so could fabricate logistics information and distort subsequent analysis. Further missing-data treatment should therefore depend on the specific downstream analytical task.

The 90% missingness threshold used in this project is a project-specific preprocessing decision rather than a universal rule. Similarly, IQR-flagged extreme durations require operational or domain validation before they can be classified as errors.

## Data Source

Metzger, A. (2015). *Cargo 2000 Freight Tracking and Tracing* [Dataset]. UCI Machine Learning Repository.

DOI: https://doi.org/10.24432/C5559K

## Conclusion

This project demonstrates that logistics preprocessing requires more than simply removing missing values. Reliable analysis depends on detecting non-standard missing-value representations, understanding the semantic meaning of variables, preserving potentially meaningful operational extremes, and applying transformations only where analytically appropriate.
