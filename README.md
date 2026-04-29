# Cardiovascular Outcomes and Race/Ethnicity in U.S. Adults  
### BRFSS 2024 · Weighted Logistic Regression · Health Equity Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Regression-green)
![Status](https://img.shields.io/badge/Project-Complete-success)

---

## 📌 Project Summary

This project examines whether race/ethnicity is associated with cardiovascular outcomes in U.S. adults using **CDC BRFSS 2024** data, while adjusting for major confounders.

- **Primary outcome:** self-reported heart attack (`CVDINFR4`)
- **Primary exposure:** CDC imputed race/ethnicity (`_IMPRACE`)
- **Modeling approach:** weighted logistic regression with cluster-robust standard errors
- **Population:** 457,670 adults (after variable subsetting from BRFSS public-use file)

> **Framing:** Race is treated as a **social/structural variable**, not a biological one. Results represent adjusted association, not causation.

---

## 🎯 Research Question

**Is there a measurable association between race/ethnicity and heart attack prevalence in U.S. adults after adjusting for diabetes status, smoking status, age group, and sex?**

---

## 🧾 Dataset

**Source:** CDC Behavioral Risk Factor Surveillance System (BRFSS) 2024  
**Input shape:** `457,670 rows × 25 selected columns` (from 301 available variables)

### Core Variables

| Role | Variable(s) |
|---|---|
| Outcome | `CVDINFR4` (heart attack history) |
| Exposure | `_IMPRACE` (6-category imputed race/ethnicity) |
| Covariates | `diabetes_status`, `smoking_status`, `_AGEG5YR`, `SEXVAR` |
| Survey design | `_LLCPWT`, `_STSTR`, `_PSU` |

---

## 🛠️ Data Engineering & Cleaning

Key preprocessing decisions from the notebook:

- Converted sentinel codes to missing where appropriate (`7`, `9`, `77`, `99`)
- Engineered **`diabetes_status`** from `DIABETE4`:
  - 0 = no diabetes
  - 1 = diabetes
  - 2 = pre-diabetes
  - gestational-only recoded to missing
- Engineered **`smoking_status`** from `SMOKE100` + `SMOKDAY2`:
  - 1 = never
  - 2 = former
  - 3 = some days
  - 4 = every day
- Rescaled `_BMI5` to standard BMI units (`/100`)
- Preserved all six `_IMPRACE` categories as coded by CDC

---

## 🔎 Missingness Audit Highlights

- `SMOKDAY2` showed high missingness due primarily to **survey skip logic** (expected)
- BMI fields had ~9% missingness with evidence of **informative missingness**
- `INCOME3` had substantial missingness (~20%) and was held out of the primary model (used in sensitivity framing)

---

## 📊 Exploratory Findings (Unadjusted)

- Heart attack prevalence differs by race/ethnicity group
- Diabetes status strongly stratifies heart attack prevalence
- Additional CVD outcomes (`CVDCRHD4`, `CVDSTRK3`, `_MICHD`) were summarized descriptively

---

## 🧠 Modeling Approach

Primary model:
- Logistic regression on heart attack outcome
- Survey-informed weighting using `_LLCPWT`
- Cluster-robust SE using `_PSU`
- Covariate adjustment for:
  - race/ethnicity
  - diabetes
  - smoking
  - age group
  - sex

---

## ⚠️ Limitations

- Self-reported outcomes and exposures
- Cross-sectional design (no causal claims)
- Potential residual confounding
- Non-random missingness in select fields

---

## 🧰 Tech Stack

- **Python 3**
- **pandas**
- **numpy**
- **matplotlib**
- **seaborn**
- **statsmodels**
- **Google Colab**

---

## 📁 Repository Structure

- `Flanders_CVO_Race_Final_Project.ipynb` — full analysis notebook
- `README.md` — project overview and methods summary

---

## ▶️ Reproducibility

1. Open notebook in Google Colab  
2. Mount Google Drive  
3. Ensure BRFSS CSV path matches notebook:  
   `/content/gdrive/MyDrive/BRFSS_2024.csv`  
4. Run all cells from a fresh runtime

---

## 👤 Author

**M. Flanders**
