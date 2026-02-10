# Suicide Rate Analysis (2000–2021) – Data Science Project

## Project Overview

This project aims to analyze **country-level suicide rates** and identify the **socio-economic, demographic, health, cultural, and environmental factors** that are most strongly associated with higher or lower suicide rates across the world.

The analysis is conducted using **Python** and standard **data science and machine learning techniques**, with a strong emphasis on **interpretability** rather than pure prediction.

⚠️ **This project is a work in progress.**  
New features, models, and analyses are continuously being added and refined.

---

## Target Variable

- **`suicide_rate`**  
  - Definition: Death rate from suicide / self-harm  
  - Unit: **Deaths per 100,000 population**
  - Source: Our World in Data (OWID)
  - Aggregation: **Mean value over the period 2000–2021**, computed for each country

---

## Dataset Structure

The final dataset (`df_merged`) is a **country-level cross-sectional dataset**, where:

- Each row represents **one country**
- Each feature represents the **average value over 2000–2021** (unless otherwise specified)
- All features are numerical and suitable for regression and tree-based models

### Time Aggregation Strategy

To reduce short-term noise and focus on **structural, long-term patterns**, all time-series variables were aggregated as:

- **Mean value between 2000 and 2021**
- If fewer years were available for a given feature, the mean was computed over the available years
- Countries without data for a given feature were retained, resulting in missing values handled during modeling via imputation

---

## Features Included

Below is a high-level overview of the main feature groups:

### Economic & Development Indicators
- `gdp_per_capita`
- `gini_index`
- `healthcare_expenditure_per_capita_ppp`
- `urban_population_pct`
- `population_density`

### Demographic Indicators
- `median_age`
- `life_expectancy`
- `one_person_households_pct`
- `literacy_rate`

### Health & Risk Factors
- `alcohol_liters_per_year`
- `drug_use_death_rate`
- `homicide_rate`
- `overweight_prevalence_pct`

### Social & Cultural Indicators
- `family_important_pct`
- `friends_important_pct`
- `religiosity_share`

### Environmental & Geographic Indicators
- `latitude`
- `avg_surface_temperature`
- `sunshine_hours_year`

### Lifestyle & Diet
- `fruit_veg_consumption_kg_per_capita`
- `meat_kg_per_capita`

---

## Modeling Approach (Current Stage)

The following models have been implemented so far:

### 1. Linear Regression
- Used to estimate **global linear associations**
- Coefficients interpreted as direction and relative strength
- Revealed clear contrasts between:
  - Demographic aging vs. health system quality
  - Risk factors vs. protective factors

### 2. Lasso Regression
- Used for **feature selection and robustness checks**
- Multiple regularization strengths (`alpha`) tested
- Results suggest that most features provide independent information
- Strong structural predictors remain stable under higher regularization

### 3. Random Forest Regression
- Used to capture **non-linear effects and interactions**
- Achieved significantly higher explanatory power (R² ≈ 0.41)
- Revealed that some variables (e.g. latitude) act as strong **partitioning proxies**
- Feature importance was validated using **permutation importance**

### 4. SHAP (in progress)
- SHAP values are being used to:
  - Explain global feature importance
  - Understand non-linear effects (e.g. latitude, age structure)
  - Provide local explanations for individual countries

---

## Preliminary Findings (Subject to Revision)

Some early patterns emerging consistently across models:

- **Higher median age** is associated with higher suicide rates once health and welfare factors are controlled for
- **Life expectancy and healthcare quality** act as strong protective factors
- **Drug-related mortality** and **single-person households** are robust risk indicators
- **Latitude** emerges as a strong non-linear proxy variable, likely capturing combined climatic, cultural, and socio-economic effects
- Purely economic indicators (e.g. GDP) appear less important once social and health factors are included

⚠️ These findings are **associative, not causal**, and should be interpreted at the **country level**.




## Disclaimer

- This is an **ecological analysis** (country-level data)
- Results do **not imply individual-level causation**
- Reporting quality and data availability vary across countries

---

## Next Steps

Planned next steps include:
- Extended SHAP analysis
- Interaction analysis and partial dependence plots
- Country clustering and typology
- Improved documentation and reproducibility

---

## Author

Davide Corbo  
(Data Science project – ongoing)
