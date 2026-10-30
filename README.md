
# Unsupervised Cardiovascular Risk Phenotyping

An empirical data science study investigating latent patient subgroups from clinical indicators using unsupervised dimensionality reduction (PCA vs. Autoencoders) and cluster analysis.



## 📌 Project Overview
Traditional heart disease risk assessment often relies on linear statistical models or binary classification, which can miss complex, non-linear relationships between clinical vitals. This project provides a controlled 2×2 benchmark comparing linear versus non-linear feature compression across centroid-based and tree-based clustering algorithms on a cardiovascular cohort (\\(N=918\\)).



## 📊 Dataset Information
* **Source:** Heart Failure Prediction Dataset (Kaggle / UCI Machine Learning Repository)
* **Cohort Size:** 918 observations, 11 clinical features + 1 target outcome (`HeartDisease`)
* **Key Features:** Age, Sex, ChestPainType, RestingBP, Cholesterol, FastingBS, RestingECG, MaxHR, ExerciseAngina, Oldpeak, ST_Slope.
* **Preprocessing:** Z-score standardization, zero-value imputation (cholesterol), and target outcome withholding for unbiased validation.



## ⚙️ Methodology Blueprint
Structured following the Electronic Health Record (EHR) phenotyping framework (*Khalid &amp; Prieto-Alhambra, 2019*) across a controlled **2×2 experimental benchmark (4 tracks)**:


              ┌─────────────────────────────────────────┐
              │ Preprocessed Patient Cohort (N = 918)   │
              └────────────────────┬────────────────────┘
                                   │
                ┌──────────────────┴──────────────────┐
                ▼                                     ▼
     Linear Reduction (PCA)                Non-Linear Reduction (Autoencoder)
      (80-85% Variance)                       (Symmetric Bottleneck)
        ┌───────┴───────┐                       ┌───────┴───────┐
        ▼               ▼                       ▼               ▼
    Track 1           Track 2               Track 3           Track 4
   k-Means        Hierarchical              k-Means        Hierarchical



### **1. Stage 1 (Feature Representation)**
* **Track A (Linear):** Principal Component Analysis (PCA) retaining 80–85% of cumulative variance.
* **Track B (Non-Linear):** Deep Autoencoder with a symmetric bottleneck architecture, trained with fixed random seed controls (`seed=42`).

### **2. Stage 2 (Phenotype Discovery)**
* Partitioning latent spaces using **\\(k\\)-Means** and **Agglomerative Hierarchical Clustering**.
* Parameter sweeps conducted across cluster counts (\\(k = 2\\) to \\(k = 6\\)).

### **3. Stage 3 (Dual-Tier Validation)**
* **Internal Geometric Quality:** Silhouette Width and Davies–Bouldin Index.
* **External Clinical Relevance:** Adjusted Rand Index (ARI) against withheld `HeartDisease` labels, and Chi-square (\\(\chi^2\\)) statistical testing (\\(p &lt; 0.05\\)) across raw clinical vitals.


