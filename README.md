# Preeclampsia-determination
This project determines the factors that are strong indicators of patients developing preeclampsia.

<img width="772" height="742" alt="image" src="https://github.com/user-attachments/assets/31900d88-f47d-4ff3-9ec1-9ffca68e0c21" />

# Summary of Feature Importance

The model identifies blood pressure, chronic hypertension, kidney disease, and diabetes as the strongest predictors of preeclampsia. These findings are consistent with established clinical knowledge and reinforce the model’s face validity.

Parity and gestational age act as protective factors, reducing predicted risk. The alignment between model coefficients and known obstetric risk factors increases confidence in the model’s interpretability and clinical relevance.

Overall, the feature importance analysis confirms that the model is leveraging meaningful physiological and historical indicators rather than spurious correlations.

## **Conclusions**

This project successfully developed a predictive model for estimating the risk of preeclampsia using a structured clinical dataset. After rigorous preprocessing, feature engineering, and model evaluation, Logistic Regression emerged as a strong and interpretable baseline model. On the expanded 5,000‑row dataset, the model demonstrated excellent performance:

- **Accuracy:** 0.999  
- **Precision:** 0.9975  
- **Recall:** 1.00  
- **F1 Score:** 0.9987  
- **ROC‑AUC:** 1.00  

These results indicate that the dataset is highly separable, with clear distinctions between patients who develop preeclampsia and those who do not. The model’s top predictors—systolic and diastolic blood pressure, chronic hypertension, chronic kidney disease, pregestational diabetes, and multiple pregnancy—align closely with established clinical risk factors. This strong agreement between model behavior and clinical knowledge enhances confidence in the model’s validity and interpretability.

The near‑perfect performance metrics likely reflect the structured and low‑noise nature of the dataset, which appears synthetic or rule‑generated. In real clinical environments, performance would be expected to be lower due to measurement variability, missing data, and overlapping risk profiles. Nonetheless, the modeling workflow, evaluation strategy, and interpretability analysis remain fully applicable to real‑world datasets.

Overall, the project demonstrates a complete and reproducible machine learning pipeline that integrates clinical reasoning, statistical rigor, and transparent model interpretation.
