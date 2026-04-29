# Key Results — Cardiovascular Outcomes and Race/Ethnicity (BRFSS 2024)

## Study Objective
Estimate whether race/ethnicity is associated with self-reported heart attack history in U.S. adults after adjustment for key risk factors.

---

## Data Summary
- **Source:** CDC BRFSS 2024 (public-use)
- **Analytic input:** 457,670 respondents
- **Primary outcome:** `CVDINFR4` (ever told had heart attack)
- **Primary exposure:** `_IMPRACE` (6-category CDC imputed race/ethnicity)
- **Core covariates:** diabetes status, smoking status, age group, sex
- **Survey design fields:** `_LLCPWT`, `_STSTR`, `_PSU`

---

## Descriptive Findings (Unadjusted)
1. Heart attack prevalence varied across race/ethnicity categories in the sample.
2. Diabetes showed a strong gradient:
   - Highest heart attack prevalence among diabetic respondents
   - Intermediate among pre-diabetic respondents
   - Lowest among non-diabetic respondents
3. Additional cardiovascular outcomes (`CVDCRHD4`, `CVDSTRK3`, `_MICHD`) were directionally consistent with elevated burden in higher-risk groups.

---

## Data Quality & Missingness Findings
- **Smoking frequency (`SMOKDAY2`) missingness:** largely explained by BRFSS skip logic (expected by survey design).
- **BMI missingness (~9%):** differed by race/outcome composition, suggesting non-random missingness.
- **Income missingness (~20%):** substantial enough to exclude from primary model and reserve for sensitivity context.

---

## Modeling Approach
- **Primary model:** weighted logistic regression for heart attack outcome
- **Adjustment set:** race/ethnicity + diabetes + smoking + age group + sex
- **Inference approach:** survey-informed weighting and cluster-robust standard errors

---

## Interpretation
- Findings support a measurable **adjusted association** between race/ethnicity and cardiovascular outcomes.
- Results should be interpreted as **associational**, not causal.
- Race/ethnicity is interpreted as a **social/structural exposure** within health inequity analysis.

---

## Limitations
- Self-reported cardiovascular outcomes
- Cross-sectional design (no temporal ordering for causal claims)
- Potential residual confounding
- Informative missingness in selected variables

---

## Practical Value
This project demonstrates:
- End-to-end epidemiologic data workflow in Python
- Complex survey handling and interpretable modeling
- Transparent missingness diagnostics and decision-making
- Clear translation of technical findings for stakeholders
