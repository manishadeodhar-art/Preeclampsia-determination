---
language:
  - en
license: cc-by-4.0
task_categories:
  - tabular-classification
task_ids:
  - tabular-multi-class-classification
  - tabular-single-column-regression
tags:
  - medical
  - synthetic
  - preeclampsia
  - eclampsia
  - maternal-health
  - africa
  - healthcare
  - pregnancy
size_categories:
  - 10K<n<100K
pretty_name: African Preeclampsia/Eclampsia Synthetic Dataset
configs:
  - config_name: default
    data_files:
      - split: train
        path: preeclampsia_africa_extra_large_10000.csv
      - split: validation
        path: preeclampsia_africa_large_5000.csv
      - split: test
        path: preeclampsia_africa_test_2000.csv
---

# African Preeclampsia/Eclampsia Synthetic Dataset
## Risk Prediction and Maternal Mortality Prevention

**Version:** 1.0  
**Release Date:** November 2024  
**Context:** Sub-Saharan African Maternal Health  
**License:** Research & Educational Use

---

## Abstract

We present synthetic datasets for preeclampsia and eclampsia prediction in Sub-Saharan Africa, generated using literature-based odds ratios from WHO systematic reviews and African cohort studies. Preeclampsia affects 5.6-9.1% of African pregnancies (higher than global 2-8%) and accounts for 14% of maternal deaths. The datasets incorporate validated risk factors with documented ORs: previous preeclampsia (OR 7.19), chronic kidney disease (OR 5.6), chronic hypertension (OR 5.1), nulliparity (OR 2.91), obesity (OR 2.47), and family history (OR 2.90). Six datasets (21,000 samples total, 5.8 MB) provide configurations for risk stratification, severity classification (mild vs severe preeclampsia vs eclampsia), and HELLP syndrome prediction. Models trained on these data are expected to achieve AUC-ROC >0.85 for preeclampsia prediction and >0.80 for severe complications, serving as proof-of-concept for antenatal screening algorithms in resource-limited African settings where preeclampsia remains a leading preventable cause of maternal mortality.

**Keywords:** Preeclampsia, Eclampsia, HELLP Syndrome, Maternal Health, Pregnancy Complications, African Health, Risk Stratification

---

## Key Features

### Clinical Parameters
- **Blood pressure**: Systolic/diastolic measurements with severity thresholds (140/90 mild, ≥160/110 severe)
- **Proteinuria**: 24-hour measurements (300-2000 mg mild, >2000 mg severe)
- **Laboratory values**: Platelets, AST/ALT, creatinine, LDH, uric acid, hemoglobin
- **HELLP syndrome markers**: Hemolysis, elevated liver enzymes, low platelets

### Risk Factors (Evidence-Based ORs)
- Previous preeclampsia: OR 7.19 (strongest predictor)
- Chronic kidney disease: OR 5.6
- Chronic hypertension: OR 5.1
- Nulliparity: OR 2.91
- Obesity (BMI >30): OR 2.47
- Family history: OR 2.90
- Multiple pregnancy: OR 2.93
- Pre-gestational diabetes: OR 3.56
- Advanced maternal age (>35): OR 1.96

### African-Specific Factors
- **Late presentation**: 60-70% present in 3rd trimester (limited antenatal care access)
- **Rural vs urban disparities**: Rural areas 1.3× higher risk, fewer antenatal visits
- **Magnesium sulfate availability**: Modeled at 70% urban, 35% rural coverage
- **Eclampsia rates**: 10-20× higher than high-income countries
- **Maternal mortality**: 3-5% of eclampsia cases in Africa vs <1% globally

### Complications Modeled
- **HELLP syndrome**: 10-20% of severe preeclampsia
- **Eclampsia**: 1-2% of preeclampsia cases (seizures)
- **Maternal death**: 0.1-5% depending on severity, access, treatment
- **Fetal growth restriction**: 10-25%
- **Placental abruption**: 1-4%
- **Acute kidney injury**: 1-5%
- **Stroke**: 0.1-0.3%

---

## Dataset Collection

### Dataset Inventory

| Dataset | N | PE Cases | Severe % | Eclampsia | Deaths | Use Case |
|---------|---|----------|----------|-----------|--------|----------|
| `preeclampsia_africa_baseline_1000` | 1,000 | 404 (40%) | 80% | 13 | 4 | Prototyping |
| `preeclampsia_africa_large_5000` | 5,000 | 2,007 (40%) | 79% | 49 | 17 | Main training |
| `preeclampsia_africa_extra_large_10000` | 10,000 | 3,941 (39%) | 79% | 78 | 34 | Deep learning |
| `preeclampsia_africa_high_risk_2000` | 2,000 | 993 (50%) | 79% | 14 | 8 | High-risk cohort |
| `preeclampsia_africa_rural_2000` | 2,000 | 887 (44%) | 78% | 16 | 9 | Rural settings |
| `preeclampsia_africa_test_2000` | 2,000 | 779 (39%) | 76% | 9 | 2 | **Validation** |

**Note:** Prevalence enriched from baseline 7.5% to 39-50% to enable model training.

---

## Expected Model Performance

### Preeclampsia Prediction
- **Logistic Regression**: AUC 0.82-0.86
- **Random Forest**: AUC 0.85-0.90
- **XGBoost**: AUC 0.87-0.92

### Severity Classification
- **Multi-class F1**: 0.75-0.82 (mild/severe/eclampsia)
- **HELLP Prediction**: AUC 0.78-0.85

### Top Predictive Features (Expected)
1. Previous preeclampsia history
2. Chronic hypertension
3. Blood pressure measurements
4. Parity (nulliparous)
5. BMI category
6. Proteinuria levels
7. Gestational age at presentation
8. Laboratory values (platelets, creatinine, LFTs)

---

## Usage Example

```python
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split

# Load data
train = pd.read_csv('preeclampsia_africa_large_5000.csv')
test = pd.read_csv('preeclampsia_africa_test_2000.csv')

# Features
features = ['age', 'parity', 'bmi', 'chronic_hypertension', 
            'pregestational_diabetes', 'previous_preeclampsia',
            'systolic_bp_mmhg', 'diastolic_bp_mmhg', 'proteinuria_24h_mg',
            'platelets_k_ul', 'creatinine_mg_dl']

X_train = train[features]
y_train = train['preeclampsia_status'].map({'Positive': 1, 'Negative': 0})

# Train model
model = RandomForestClassifier(n_estimators=100, class_weight='balanced')
model.fit(X_train, y_train)

# Expected AUC: 0.85-0.90
```

---

## Limitations

**What This Dataset IS:**
- ✅ Antenatal risk stratification training
- ✅ Severity prediction modeling
- ✅ Healthcare access disparity analysis
- ✅ Sample size planning for prospective studies

**What This Dataset IS NOT:**
- ❌ Replacement for blood pressure monitoring
- ❌ Including longitudinal BP trajectories
- ❌ Capturing postpartum preeclampsia
- ❌ Validated for clinical decision-making without prospective trials

**Mandatory Next Steps:**
1. Prospective validation in African antenatal clinics
2. Integration with routine BP monitoring protocols
3. Healthcare worker training on interpretation
4. Ethical approval for clinical deployment

---

## Citation

```
African Preeclampsia Synthetic Dataset (2024)
Risk-based prediction for maternal mortality prevention
Version 1.0, Generated November 2024
Organization: Electric Sheep Africa
License: CC-BY-4.0
```

**Primary Sources:**
- WHO Systematic Review: Preeclampsia Risk Factors (ORs)
- African Maternal Health Cohorts (Nigeria, Ghana, Kenya)
- HELLP Syndrome Meta-Analysis
- Eclampsia Mortality Data (Sub-Saharan Africa)

---

## Quick Reference

**Core Features (11):**
```python
features = ['age', 'parity', 'bmi', 'chronic_hypertension',
            'systolic_bp_mmhg', 'diastolic_bp_mmhg', 
            'proteinuria_24h_mg', 'platelets_k_ul',
            'ast_u_l', 'creatinine_mg_dl', 'previous_preeclampsia']
```

**Targets:**
- Binary: `preeclampsia_status` (Positive/Negative)
- Severity: `severity` (None/Mild/Severe)
- Complications: `eclampsia`, `hellp_syndrome`, `maternal_death`

**Expected Performance:**
- Preeclampsia prediction: AUC 0.85-0.92
- Severe complication risk: AUC 0.78-0.86

---

**Status:** Research Use Only - Prospective Validation Required  
**Last Updated:** November 7, 2024  
**Contact:** https://huggingface.co/electricsheepafrica
