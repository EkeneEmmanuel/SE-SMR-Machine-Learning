# A Multi-Output Machine Learning Approach to Sorption-Enhanced Steam Methane Reforming

[![Publication](https://img.shields.io/badge/Publication-JASPE%202026-blue)](https://doi.org/10.33736/jaspe.11153.2026)
[![Research](https://img.shields.io/badge/Research-Machine%20Learning-orange)]()
[![Domain](https://img.shields.io/badge/Domain-Hydrogen%20%7C%20Carbon%20Capture-green)]()

Machine learning models for predicting key performance indicators in **sorption-enhanced steam methane reforming (SE-SMR)**, including methane conversion, hydrogen yield, hydrogen purity, and carbon dioxide capture.

**Publication:** Ekene E. Iwuchukwu and Adegboyega B. Ehinmowo  
**Journal:** *Journal of Applied Science & Process Engineering*, Vol. 13, No. 2, 2026, pp. 105–130  
**DOI:** [10.33736/jaspe.11153.2026](https://doi.org/10.33736/jaspe.11153.2026)

---

## 1. Project Overview

Conventional steam methane reforming (SMR) is a major route for hydrogen production, but it is associated with substantial carbon dioxide emissions. Sorption-enhanced steam methane reforming integrates CO₂ capture into the reforming process. A solid sorbent captures CO₂ as it is produced, helping shift the reaction equilibrium toward higher methane conversion and hydrogen purity.

This project applies supervised machine learning to predict four important SE-SMR performance indicators. Unlike approaches that focus on a single process output, this study considers methane conversion, hydrogen yield, hydrogen purity, and CO₂ capture within a paired multi-output modelling framework.

### Modelling Strategy

The study adopts a dual multi-output modelling strategy:

| Model Group | Prediction Outputs |
|---|---|
| Model Group 1 | Methane conversion and hydrogen yield |
| Model Group 2 | Hydrogen purity and CO₂ capture |

The paired outputs reflect related process mechanisms. Methane conversion and hydrogen yield are associated with catalytic kinetics and thermodynamic equilibrium, while hydrogen purity and CO₂ capture are influenced by adsorption–desorption behaviour.

## 2. Project Objectives

- Develop machine learning models for predicting four SE-SMR performance indicators.
- Compare the predictive performance of six regression algorithms.
- Optimise model hyperparameters using Bayesian optimisation.
- Evaluate model performance using regression metrics.
- Examine relationships between operating conditions and process performance.

## 3. Dataset

The study uses **121 data points** collated from two published SE-SMR simulation studies:

- Antzara et al.
- Faheem et al.

The source studies used Aspen Plus simulations to investigate the effects of process operating parameters.

To improve consistency between the two sources, data harmonisation was performed. Hydrogen yield values were converted to a methane-consumed basis, while pressure values reported in atmospheres were converted to bar.

### Input Features

| Feature | Description | Unit |
|---|---|---|
| Reformer Temperature | Operating temperature of the reformer | °C |
| Reformer Pressure | Operating pressure of the reformer | bar |
| Steam-to-Carbon Ratio (S/C) | Molar steam-to-carbon ratio | Dimensionless |
| Calcium Oxide-to-Carbon Ratio (CaO/C) | Sorbent-to-carbon ratio | Dimensionless |

### Prediction Targets

| Target | Description | Unit |
|---|---|---|
| Methane Conversion | Fraction of inlet methane converted | % |
| Hydrogen Yield | Hydrogen yield on a methane-consumed basis | % |
| Hydrogen Purity | Hydrogen fraction in the product gas | % |
| CO₂ Capture | Fraction of carbon dioxide captured | % |

### Data Preparation

The following preprocessing steps were reported:

1. Data collation from the two literature sources.
2. Harmonisation of hydrogen yield and pressure units.
3. Data cleaning and outlier removal.
4. Min-max normalisation of input features.
5. Shuffling of observations.
6. Division into training and test subsets using an 80:20 split.

**Dataset considerations:**

- Total observations: 121.
- Data were obtained from published simulation studies rather than operational plant measurements.
- Residence time and catalyst properties were excluded because they were unavailable in the adopted dataset.
- The publication does not provide a direct dataset download link.

## 4. Methodology

The project workflow can be summarised as follows:
1. **Data collation:** Obtain SE-SMR simulation data from the two cited literature sources.
2. **Data harmonisation:** Convert hydrogen yield to a methane-consumed basis and convert pressure units to bar.
3. **Data preparation:** Clean the data, remove outliers, normalise input features with min–max scaling, and shuffle observations.
4. **Train–test split:** Divide the dataset into training and test subsets using an 80:20 ratio.
5. **Multi-output model construction:** Train one model group for methane conversion and hydrogen yield, and another for hydrogen purity and CO₂ capture.
6. **Hyperparameter tuning:** Apply Bayesian optimisation, using 100 trials as reported in the study.
7. **Model evaluation:** Compare predictions with actual values using regression metrics.
8. **Relationship analysis:** Examine correlations and feature-importance patterns to understand the influence of operating conditions.

## 5. Model evaluation

The study reports the use of the following regression metrics:
- **R² (coefficient of determination):** Measures how well predictions explain the variance in observed values. Higher values indicate a better fit.
- **RMSE (root mean squared error):** Measures the typical magnitude of prediction errors while penalising larger errors more strongly.
- **MSE (mean squared error):** Average squared prediction error.
- **MAPE (mean absolute percentage error):** Expresses prediction error relative to actual values as a percentage.

## 6. Machine Learning Models

Six regression algorithms were evaluated.

| Algorithm | Description |
|---|---|
| Linear Regression | Baseline regression model |
| Support Vector Machine (SVM) | Nonlinear regression using an RBF kernel in the reported tuned models |
| Decision Tree | Tree-based regression |
| Random Forest | Ensemble of decision trees |
| CatBoost | Gradient-boosted decision trees |
| LightGBM | Gradient-boosted decision trees using leaf-wise growth |

## 7. Key Results
The published study reports strong predictive performance across the four target variables.

| Prediction target | Best-performing model | Test R² | Test RMSE |
|---|---|---:|---:|
| Methane conversion | Support Vector Machine | 0.993 | 0.973% |
| Hydrogen yield | Support Vector Machine | 0.988 | 0.514% |
| Hydrogen purity | Support Vector Machine | 0.979 | 1.187% |
| CO₂ capture | Random Forest | 0.996 | 2.059% |

## 8. Limitations

- The dataset contains 121 observations, which is relatively small for training and assessing machine-learning models.
- The data were collated from two simulation studies rather than a large operational plant dataset.
- Residence time and catalyst properties were excluded because the source dataset did not provide them.
- The 80:20 train–test split provides a held-out test set, but does not by itself establish performance across different plants, operating regimes, or real-time industrial conditions.
- Strong test-set metrics do not alone demonstrate deployment readiness. Further validation using independent data and operational measurements would be needed.

## 9. Publication and citation
If you use this work, please cite the published article:

Iwuchukwu, E. E., & Ehinmowo, A. B. (2026). A Multi-Output Machine Learning Approach to Sorption-Enhanced Steam Methane Reforming. Journal of Applied Science & Process Engineering, 13(2), 105–130. https://doi.org/10.33736/jaspe.11153.2026
