#  LoanTap - Credit Risk Analytics Using Logistic Regression & LightGBM


A complete end-to-end credit risk analysis and machine-learning project designed to predict borrower default for a financial lending platform. This project includes data cleaning, feature engineering, model development, threshold optimization, business evaluation, and actionable risk recommendations.

---
 ## Project Overview

Financial institutions face significant loss when risky customers default on loans.
This project builds a **predictive model** to identify high-risk borrowers before loan approval.

Two models were developed and compared:

- **Logistic Regression** (baseline model)

- **LightGBM** (final selected model)

The final model helps optimize loan approvals, reduce NPAs, and improve credit decision-making.

---

##  Project Objectives
- Predict loan defaults with high recall to minimize **missed risky borrowers**.  
- Compare interpretable vs. high-performance ML models.  
- Perform feature engineering to enrich borrower behavioral patterns.  
- Determine an **optimal decision threshold** for business use.  
- Provide a full business-level **Credit Risk Strategy Recommendation**.

---

## 🧭 End-to-End Workflow

```
flowchart LR
A[Data Collection] --> B[EDA & Cleaning]
B --> C[Feature Engineering]
C --> D[Train-Test Split]
D --> E[Model 1: Logistic Regression]
D --> F[Model 2: LightGBM]
E --> G[Model Evaluation]
F --> G
G --> H[Threshold Optimization]
H --> I[Business Insights & Reporting]
```
---


## Dataset Summary

The dataset has **~400k** Datapoints including features like borrower financial details, repayment history, loan characteristics, and credit profile.

Key features include:

- loan amount, annual income, installment, interest rate

- dti, revol_bal, grade, purpose, 
- loan_status (target variable)

Target encoding:

- 1 = Good borrower

- 0 = Defaulter
---

## Data Preprocessing

- Missing value handling

- Outlier treatment

- Categorical feature encoding

- Standarization

- Train/validation/test split

- SMOTE used for Logistic Regression

- Imbalance handled using scale_pos_weight in LightGBM

## Feature Engineering

Created new financial stress indicators for better prediction:
```
loan_to_income_ratio = loan_amnt / annual_inc * installment / int_rate
dti_over_revolbal = dti / (revol_bal * grade)
```

These features improved model recall and AUC.

---
## Models Built
 #### **Logistic Regression**

- Baseline model

- Applied SMOTE

- Limited non-linearity handling

- Recall and precision remained low

#### **LightGBM (Final Model)**

- Gradient boosting decision trees

- Handles imbalance well

- More robust on non-linear financial features

- Tuned hyperparameters & early stopping
---

##  Model Performance Summary

| Model | ROC–AUC | Optimal Threshold | Precision | Recall | Remarks |
|-------|---------|-------------------|-----------|--------|---------|
| **Logistic Regression** | 0.68 | 0.5 | 0.32 | 0.56| Good interpretable baseline |
| **LightGBM** | 0.70  | 0.63 | 0.25 | 0.85 | Stronger performance, captures non-linear patterns |

> **LightGBM clearly outperforms Logistic Regression** and is better suited for production deployment.

---
## Model Visualizations

### ROC–AUC Curve
![ROC Curve](visual_Images\ROC-AUC_curve.png)

### Confusion Matrix
![Confusion Matrix](visual_Images\Confusion_matrix.png)

### Feature Importance (LightGBM)
![Feature Importance](visual_Images\Feature_importance.png)

---
## Threshold Optimization 

To minimize losses, high Recall is prioritized so risky borrowers are not approved.

- Threshold ≈ 0.63 gives:

  - Precision: 25%

  - Recall: 85%

- Recommended for **risk-averse lending** (fintech/loan startups).
---
## Business Insights

- High recall reduces missed defaulters, lowering loss.

- Customers with high DTI, high revolving balance and low income show higher risk.

- Borrowers in lower grades (E, F, G) show increased default probability.

- Risk-based decision tiers can be implemented:

| Risk Level |	Threshold |	Business Action |
|---|----|---|
| High Risk	|≥ 0.63	|Manual verification or rejection
| Medium Risk|	0.40 – 0.63	|Additional documentation
| Low Risk	|< 0.40	Fast-track | approval
---

## Recommendation to Business

- Integrate LightGBM model into loan approval workflow

- Use threshold tuning dashboard for real-time adjustments

- Improve income verification and credit utilization data collection

- Introduce dynamic pricing based on predicted risk
---

##  Repository Structure
```
├── Dataset/
|   └──  LoanTap
├── notebooks/
│   └── LoanTap.ipynb
|   └── LoanTap.html
|
├── visual_Images/
│   └── Classification_report.png
│   └── Confusion_matrix.png
│   └── Feature_importance.png
|   └── ROC-AUC_curve.png
|
├── Business_Report-LoanTap.pdf
│      
├── README.md
├── requirements.txt

```

---

##  Tech Stack
- **Python**
- **Pandas, NumPy**
- **Matplotlib, Seaborn**
- **Scikit-Learn**
- **LightGBM**
- **Jupyter Notebook**

## Installation
```
git clone https://github.com/Manishnandi0006/LoanTap_Credit-risk_prediction
cd LoanTap_Credit-Risk_prediction
pip install -r requirements.txt
```

## Requirements
```
pandas
numpy
matplotlib
seaborn
scikit-learn
lightgbm
plotly
```



---
## License

This project is licensed under the MIT License.



##  Contact
If you'd like to collaborate or discuss credit-risk analytics, feel free to reach out!

Manish Nandi , Data analyst

📧 mannsqurz@gmail.com

🔗 [LinkedIn](https://www.linkedin.com/public-profile/settings?trk=d_flagship3_profile_self_view_public_profile&lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base%3BIwKCjSvEQOu27Xm0LTZtmQ%3D%3D)
