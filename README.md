# Unsupervised Cardiovascular Risk Phenotyping

An empirical data science study investigating latent patient subgroups from clinical indicators using unsupervised dimensionality reduction and cluster analysis.

## Dataset
* **Source:** Heart Failure Prediction Dataset (Kaggle / UCI Machine Learning Repository)
* **Cohort Size:** 918 observations, 11 clinical features + 1 outcome label
* **Key Indicators:** Age, Resting Blood Pressure, Serum Cholesterol, Fasting Blood Sugar, Maximum Heart Rate, Exercise Angina, ST-segment depression (Oldpeak), and ST Slope.

## Methodology Blueprint
Structured following the two-stage Electronic Health Record (EHR) phenotyping framework (Khalid & Prieto-Alhambra, 2019):
1. **Stage 1 (Feature Representation):** Unsupervised dimensionality reduction and variable contribution analysis using PCA.
2. **Stage 2 (Phenotype Discovery):** Clustering (k-Means, Hierarchical) to discover distinct cardiovascular risk profiles.
3. **Stage 3 (Clinical Validation):** Internal evaluation (Silhouette, Calinski-Harabasz) and external profiling against known cardiac outcomes.
