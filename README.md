# Statins & LDL‑C: Sex and Age Effects (UK Biobank)

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas)![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)![matplotlib](https://img.shields.io/badge/matplotlib-2C5BB4?style=for-the-badge&logo=matplotlib&logoColor=white)![seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=Seaborn&logoColor=white)

**Authors**: Ron Raviv and Danielle Shany  
**Advisors**: Prof. Adi Shraibman, Prof. Gidon Dror, Dr. Dorit Shweiki, Dr. Yonatan Bilu  
**Institution**: The Academic College of Tel Aviv‑Yaffo

## Overview

This project examines **gender‑specific responses to statin therapy** using the UK Biobank cohort. We study how statin use is associated with **lipid markers** (LDL‑C, HDL‑C, Triglycerides) and an **inflammatory marker** (CRP), and whether the associations **differ between men and women**. The analysis compares **statin users vs. non‑users** in a large observational dataset and summarizes subgroup differences with simple, interpretable models.

## Dataset

- **Source**: UK Biobank (large, population‑based research resource)
- **Participants**: ~**430,000** participants derived from the UK Biobank cohort
- **Age Range**: Adults, average age **56**
- **Key Features** (selected):
  - **Demographics**: Gender, Age
  - **Lifestyle**: Smoking status, Moderate activity, BMI
  - **Clinical measurements**: SBP, DBP, Diabetes status
  - **Lipid profile**: HDL‑C, LDL‑C, Triglycerides
  - **Liver function markers**: Albumin, ALP, ALT, AST, GGT, Total bilirubin
  - **Inflammation & medication**: CRP, Statin use
- **Design note**: The dataset **does not include before/after** measurements around statin initiation. We therefore compare **users vs. non‑users**; this limits causal interpretation but is common in large‑scale observational studies.

## Project Goals

1. **Quantify** statin‑associated differences in **LDL‑C, HDL‑C, TG, and CRP**.
2. **Compare** effects **between men and women**.
3. **Assess** alignment with prior literature on sex‑specific statin responses.

## Data Preprocessing

- **Co‑linearity reduction** via **VIF‑based feature removal**.
- **Missing values**: impute where appropriate; drop high‑null records.
- **Categorical features**: One‑Hot Encoding.
- **Transformations**: apply **log transformation** to skewed variables (e.g., CRP).

## Model Selection and Training

- **Model family**: **Linear regression** with interpretable coefficients.
- **Specification**: four **sex‑stratified** models, each targeting a single marker:
  - **LDL‑C**, **HDL‑C**, **Triglycerides (TG)**, **CRP** (log‑transformed).
- **Comparisons**: primary coefficient of interest is the **statin use** indicator; models are estimated separately in **men** and **women** and adjusted with available covariates as needed for robustness.

## Results

Key cross‑sectional findings from the sex‑stratified analyses:

- **LDL‑C**: **larger reduction in men** relative to women among statin users.
- **HDL‑C**: women’s HDL levels among users **remain closer to non‑users** than men (i.e., men show a larger decrease).
- **Triglycerides**: **higher TG among statin users**, **especially men**.
- **CRP**: evidence of an **anti‑inflammatory benefit** for both sexes, **smaller in women**.

Where relevant, we compare these patterns with prior findings reported in the literature review (e.g., Zhang 2022; Moriarty 2017) and note areas of agreement and divergence.

## Conclusion

Statins are prescribed first and foremost to **lower LDL‑C** and thereby reduce cardiovascular risk. In our UK Biobank–based analysis, the **clearest and most clinically relevant signal** is the LDL‑C difference: statin users have **lower LDL‑C** than non‑users, with a **larger reduction in men than in women**. Other biomarkers (HDL‑C, triglycerides, CRP) show secondary, sex‑dependent patterns, but they do not change the central takeaway: the principal effect—and primary reason for treatment—is **LDL lowering**, with evidence that the **magnitude of this LDL response differs by sex**. These findings support sex‑aware evaluation of statin therapy and motivate future work to understand mechanisms (dose, adherence, body size, selective prescribing) and clinical implications.

**Limitations**: observational design without pre/post measurements limits causal claims; potential residual confounding.
