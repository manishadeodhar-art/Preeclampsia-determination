# Preeclampsia Risk Prediction Using Machine Learning
A Capstone Project for the UC Berkeley Machine Learning & AI Program

## Project Overview
Preeclampsia is a serious hypertensive disorder of pregnancy that can lead to severe maternal and fetal complications if not detected early. This project builds a machine‑learning–based early‑risk prediction system using structured clinical data. The goal is to support clinicians with an interpretable, data‑driven tool that identifies high‑risk pregnancies before symptoms escalate.

This capstone project applies the full CRISP‑DM lifecycle — from data understanding and preprocessing to model development, evaluation, and deployment‑ready pipelines.

## Business Objective
- Early identification of preeclampsia risk enables:

- Timely clinical intervention

- Increased monitoring for high‑risk patients

- Improved maternal and neonatal outcomes

- Reduced healthcare burden from emergency interventions

The objective is to develop a clinically interpretable, accurate, and deployable model that predicts whether a pregnant patient is at risk of developing preeclampsia.

## Dataset
The dataset includes structured maternal clinical features such as:

- Demographics (age, gravida, parity)

- Medical history (chronic hypertension, diabetes, kidney disease)

- Obstetric history (previous preeclampsia, family history)

- Pregnancy‑specific indicators (antenatal visits, multiple pregnancy)

- BMI and obesity flags

- Interaction terms (Age × BMI, BP × BMI)

- The target variable is preeclampsia diagnosis (0/1).

## Data Preprocessing
Key preprocessing steps:

Handling missing values 

Encoding categorical variables

Creating clinically meaningful binary flags

Engineering interaction terms

Scaling numerical features

Splitting into training and test sets

Selecting top features based on coefficient magnitude

## Exploratory Data Analysis (EDA)
A comprehensive Exploratory Data Analysis (EDA) was conducted to understand the structure, quality, and clinical patterns within the dataset before modeling. The EDA focused on identifying trends, distributions, correlations, and potential risk indicators relevant to preeclampsia.

### Key EDA Steps
- Initial Inspection: Reviewed dataset shape, data types, summary statistics, and unique values

- Missing Value Analysis: Identified missingness patterns and assessed whether imputation or feature removal was required.

- Distribution Analysis: Visualized distributions of key clinical variables such as age, BMI, gestational age, and antenatal visits.

- Risk Factor Exploration: Compared distributions of known risk factors (e.g., chronic hypertension, diabetes, nulliparity) between preeclampsia and non‑preeclampsia groups.

- Correlation Heatmap: Examined relationships among numerical features to detect multicollinearity and clinically meaningful associations.

- Class Balance Check: Assessed the distribution of the target variable to understand imbalance and inform model selection and evaluation.

- Feature Engineering Validation: Verified the behavior of engineered features such as obesity flags, interaction terms, and parity indicators.

### Insights from EDA
- Preeclampsia cases showed higher prevalence of chronic hypertension, obesity, and nulliparity.

- Blood pressure–related features exhibited strong correlations with the target variable.

- The dataset showed moderate class imbalance, reinforcing the need for balanced class weights during modeling.

- Engineered features (e.g., BMI obesity flag, age × BMI interaction) improved separation between risk groups.

- No severe multicollinearity was observed after feature selection and engineering.

- The EDA provided the clinical and statistical foundation for feature engineering, model selection, and interpretation throughout the project.

## Models Developed
Five models were trained and evaluated:

- Logistic Regression (Default)

- Logistic Regression (Tuned)

- Logistic Regression (Selected Features)

- Random Forest Classifier

- XGBoost Classifier

Each model was evaluated using:

- Accuracy

- Precision

- Recall

- F1‑Score

## Model Performance Summary
![Model Performance Comparison](https://github.com/user-attachments/assets/04bcd832-b4dd-44f1-9d54-144f4ffba2f6)

![Model Comparison Bar chart](https://github.com/user-attachments/assets/fe214e8a-82bf-4e34-a6e2-517b51c63be6)


### Conclusion:  
XGBoost performs best overall, but Logistic Regression (Tuned) offers the best balance of performance and interpretability — making it ideal for clinical use.

## Feature Importance (Top Predictors)
The tuned Logistic Regression model identified the following as the strongest predictors of preeclampsia:

![Top Feature Coefficients](https://github.com/user-attachments/assets/f07297bb-a8e8-47ba-926d-ae40ab087073)


### Top Risk‑Increasing Factors
- Nulliparity

- Chronic hypertension

- Family history of preeclampsia

- Previous preeclampsia

- Obesity (BMI obesity flag)

- Chronic kidney disease

- Antiphospholipid syndrome

- Pregestational diabetes

- Multiple pregnancy

### Protective Factors
- Increased antenatal visits

- Multiparity

- Later gestational age

These align closely with established clinical research, increasing confidence in the model’s validity.

## Model Pipeline & Deployment
A full scikit‑learn Pipeline was built to:

- Select the top 10 most important features

- Scale inputs

- Train a tuned Logistic Regression model

- Save the pipeline as a .pkl file

- A reusable prediction function allows clinicians or applications to input patient data and receive:

- A binary prediction

- Probability of preeclampsia

This makes the model ready for integration into dashboards, clinical decision support tools, or mobile apps.
## How to Use the Prediction Pipeline

![Sample Patient](https://github.com/user-attachments/assets/c23bc3ea-0de4-4bd8-817c-905a7d5f4443)


## Deployment
This project includes a fully trained and serialized machine‑learning pipeline (preeclampsia_top10_pipeline.pkl) that can be integrated into real applications. The pipeline handles preprocessing, feature selection, scaling, and prediction in one step, making it suitable for deployment in:

- Web service APIs (FastAPI, Flask, Django REST)

- Cloud functions (AWS Lambda, Azure Functions)

- Clinical dashboards or mobile health apps

A typical API workflow:

- Receive patient data as JSON

- Load the saved pipeline

- Run prediction

- Return risk score + probability

This enables real‑time preeclampsia risk assessment in digital health systems.

### Medical Recommendation Integration
While the model does not provide medical advice, it can support:

- Early‑risk stratification

- Automated alerts for high‑risk patients

- Enhanced antenatal monitoring workflows

- Decision‑support tools for clinicians

The model highlights clinically meaningful predictors (e.g., chronic hypertension, nulliparity, obesity), helping care teams tailor follow‑up and counseling.

### Limitations
- Dataset‑specific: Performance may vary across populations or healthcare settings.

- Feature scope: Biomarkers and Doppler measurements are not included.

- Static predictions: The model does not track changes over time.

- Not diagnostic: Outputs are risk estimates, not medical diagnoses.

## Conclusion
This project demonstrates how machine learning can support early detection of preeclampsia using clinically interpretable features. The tuned Logistic Regression model provides strong predictive performance while maintaining transparency — a critical requirement for healthcare applications.

The final pipeline is lightweight, deployable, and ready for integration into real‑world clinical workflows.

Jupyter Notebook: https://github.com/manishadeodhar-art/Preeclampsia-determination/blob/main/Investigation.ipynb
