Cardiac Treatment Cost Prediction & Package Pricing Strategy

Overview

This project addresses a real-world healthcare business problem faced by a cardiac specialty hospital transitioning from traditional post-treatment billing to a Fixed Package Pricing model.

Under this model, patients receive an upfront treatment quote before admission that is expected to cover the overall cost of their treatment.

The challenge is balancing two risks:

* Under-pricing: The hospital may lose money on complex, high-cost patients.
* Over-pricing: The package may become unattractive compared with competing hospitals.

The objective of this project was therefore not only to predict treatment cost, but to build an end-to-end Data Science and Decision Support solution that connects:

Patient Data → Cost Prediction → Explainability → Risk Stratification → Package Pricing → Business Decision

⸻

Business Problem

The hospital needs to answer several critical questions before adopting fixed package pricing:

1. Can treatment cost be predicted from available patient information?
2. What factors are the strongest drivers of treatment cost?
3. Which patient segments represent the highest financial risk?
4. What package price points could be considered?
5. Should the hospital adopt fixed package pricing?
6. What risk-management strategies are required?
7. What additional data should be collected to improve future predictions?

⸻

Project Objectives

The project was designed around four main deliverables:

1. Cost Predictive Model

Build and evaluate machine learning models capable of predicting total hospital treatment cost.

2. Statistical & Exploratory Analysis

Understand the dataset, identify patterns, test hypotheses, analyze correlations, and assess statistical significance.

3. Power BI Decision Support Dashboard

Transform model outputs and analytical findings into an interactive dashboard for management.

4. Business Report

Translate the technical results into practical recommendations around package pricing, risk management, and future data requirements.

⸻

Dataset

The dataset contains 248 cardiac patient records and 24 initial features.

The available information covers several categories:

Patient Information

* Age
* Gender
* Weight
* Height

Clinical Information

* Blood Pressure
* Heart Rate
* Hemoglobin
* Creatinine
* Other clinical biomarkers

Admission Context

* Admission type
* Emergency vs Elective admission
* Other admission-related information

Hospitalization

* Total Length of Stay
* ICU Stay
* Ward Stay

Implant Information

* Implant usage
* Implant-related cost

Target Variable

Total Cost to Hospital

This represents the total treatment cost incurred by the hospital.

⸻

Project Workflow

The complete workflow followed an end-to-end Data Science approach:

Raw Patient Data
        ↓
Data Understanding
        ↓
Data Quality Assessment
        ↓
Exploratory Data Analysis
        ↓
Statistical Analysis
        ↓
Feature Engineering
        ↓
Data Preparation
        ↓
Model Development
        ↓
Model Comparison
        ↓
Model Evaluation
        ↓
SHAP Explainability
        ↓
Risk Stratification
        ↓
Package Pricing Strategy
        ↓
Power BI Dashboard
        ↓
Business Recommendations

⸻

1. Data Understanding & EDA

The first stage focused on understanding the structure and quality of the data.

The analysis covered:

* Data types
* Missing values
* Duplicate records
* Distribution of numerical variables
* Categorical variables
* Outlier detection
* Cost distribution
* Correlation analysis
* Relationships between clinical variables and treatment cost

One important consideration during this stage was the interpretation of outliers.

In healthcare data, an outlier is not necessarily an error.

For example, a patient with an unusually long ICU stay or very high implant cost may represent a clinically valid high-complexity case.

Therefore, clinically meaningful observations were not automatically removed.

⸻

2. Cost Distribution Analysis

The treatment cost showed substantial variation across patients.

The observed treatment cost ranged approximately from:

₹46K → ₹887K

This represents roughly a 19x difference between the lowest and highest observed treatment costs.

This finding highlighted a major business risk:

A single flat package price may not adequately represent the variation in patient treatment complexity.

This supported the need for a differentiated pricing framework.

⸻

3. Feature Engineering

Five engineered features were created to capture additional clinical and operational signals:

* BMI
* ICU Ratio
* Ward Ratio
* Implant Flag
* Emergency Flag

The goal of feature engineering was not simply to increase the number of variables.

Instead, the objective was to transform raw patient information into features that better represent:

* Clinical complexity
* Hospital resource utilization
* Implant exposure
* Admission context
* Treatment intensity

⸻

4. Statistical Analysis

Statistical analysis was performed to validate relationships discovered during exploratory analysis.

The analysis included:

* Correlation Analysis
* Hypothesis Testing
* Independent t-test
* ANOVA
* Statistical significance testing

One important finding was the difference in treatment cost between Emergency and Elective admissions.

The statistical test produced approximately:

p ≈ 0.0004

This provided statistical support for treating emergency admissions differently within the pricing framework.

⸻

5. Machine Learning

Three models were developed and compared:

Linear Regression

Used as an interpretable baseline and to understand linear relationships between features and treatment cost.

Random Forest

Used to capture nonlinear relationships and interactions between clinical and operational variables.

XGBoost

Used as a gradient boosting benchmark for nonlinear prediction.

⸻

6. Model Evaluation

Models were evaluated using multiple metrics rather than relying on a single score.

Evaluation metrics included:

* R²
* MAE
* RMSE
* 5-Fold Cross Validation

Final Test Performance

The Random Forest achieved the strongest held-out test performance:

Metric	Result
R²	0.692
MAE	₹40,513
RMSE	₹76,570

Based on the held-out test results, Random Forest was selected as the final point-prediction model.

However, cross-validation provided an important additional perspective.

Linear Regression achieved a higher mean cross-validation R²:

CV Mean R² = 0.819

This highlighted an important modeling lesson:

Model selection should not depend on a single performance metric.

With a relatively small dataset, generalization, stability, interpretability, and business suitability must all be considered.

⸻

7. Model Explainability with SHAP

Prediction alone was not enough.

The next question was:

Why is the model predicting this treatment cost?

SHAP was used to interpret feature contributions and identify the major cost drivers.

The analysis showed:

Feature	Contribution
ICU Stay	69.6%
Implant Cost	10.4%

Together, ICU Stay and Implant Cost represented approximately 80% of the model’s predictive power.

In contrast, demographic variables such as Age and Gender had contributions of less than 1%.

Business Insight

The findings suggest that package pricing should focus primarily on:

Clinical and procedural complexity

rather than demographic characteristics.

⸻

8. Important Modeling Challenge

One of the most important limitations identified during the project was the timing of certain variables.

Variables such as:

* ICU Stay
* Total Length of Stay

are only fully known after treatment has progressed.

Therefore, there is an important distinction between:

Predicting cost after knowing what happened

and:

Predicting cost early enough to support a real pricing decision.

This is an important direction for the next iteration of the solution.

The future version should focus on early-stage prediction using admission-time features wherever possible.

⸻

9. Risk Stratification

The predicted treatment costs were converted into three financial risk segments:

* Low Risk
* Medium Risk
* High Risk

The final distribution was:

Risk Tier	Distribution
Low Risk	5.6%
Medium Risk	81.5%
High Risk	12.9%

This allowed the project to move from simple prediction toward practical business decision-making.

Instead of:

Predicted Cost = X

the system becomes:

Patient
   ↓
Predicted Cost
   ↓
Risk Tier
   ↓
Recommended Package

⸻

10. Package Pricing Strategy

A three-tier pricing framework was developed using segment-level median treatment cost combined with a 25% financial buffer.

The resulting package price points were:

Package	Recommended Price
Standard	₹106,344
Advanced	₹210,621
Complex	₹548,186

The 25% buffer was designed to absorb part of the cost variation within each segment and reduce the risk of under-pricing higher-complexity cases.

⸻

11. Power BI Dashboard

The analytical results were transformed into an interactive Power BI Decision Support Dashboard.

The dashboard focuses on making the ML outputs understandable and actionable for management.

Key dashboard components include:

* Cost Distribution
* Risk Tier Breakdown
* Cost Drivers
* Emergency vs Elective Analysis
* Implant Impact
* Patient-level Insights
* Cost and Risk Metrics
* Decision-support indicators

The objective was not simply to create visualizations.

The objective was:

Turn model outputs into information that decision-makers can actually understand and use.

⸻

12. Business Report

The final stage was translating the technical analysis into a business-oriented report.

The report addressed the core management questions:

Should the hospital adopt package pricing?

Yes, but with a structured risk-tiered pricing framework rather than a single flat price.

What pricing strategies can reduce financial risk?

Recommended approaches included:

* Emergency premium
* Implant-inclusive packages
* Implant-exclusive packages
* ICU cost controls
* Biomarker-based escalation
* Regular model monitoring

Which patients represent the highest risk?

Patients associated with higher clinical complexity, ICU utilization, and implant-related costs represent greater financial risk.

What additional data would improve future predictions?

Priority data additions include:

* Procedure / Surgery Type
* Payer Type
* Diagnosis Code
* Comorbidity Information

These variables could provide stronger information about treatment complexity and improve future pricing models.

⸻

Key Business Insights

The project produced several important insights:

1. Treatment cost varies significantly

A roughly 19x difference between observed minimum and maximum cost makes a single flat package price risky.

2. ICU utilization is a major cost driver

ICU Stay represented approximately 69.6% of the model’s feature importance.

3. Implant cost is another major driver

Implant Cost contributed approximately 10.4%.

4. Emergency cases require different treatment

Emergency admissions showed significantly higher costs than elective admissions.

5. Risk segmentation can support pricing

A three-tier risk framework provides a more practical alternative to a single universal package price.

6. Explainability matters

SHAP helped connect model predictions to understandable business and clinical factors.

⸻

Key Takeaway

The central lesson from this project was:

The model is not the product. The decision system is the product.

The Notebook, Machine Learning model, statistical analysis, SHAP explainability, Power BI dashboard, and Business Report were all parts of one larger solution.

The real value came from connecting them:

Data
→ Insight
→ Prediction
→ Explainability
→ Risk
→ Pricing
→ Decision
→ Business Value

This project reinforced the idea that a Data Scientist should not only build accurate models, but also understand how those models can support real-world decisions.

⸻

Future Improvements

The next stage of development would focus on moving the project toward a more production-ready solution.

Planned improvements include:

* Early-stage cost prediction using admission-time features
* Larger and richer clinical datasets
* Procedure-specific pricing
* Real-time prediction
* API integration
* Model monitoring
* Data drift detection
* Automated retraining
* Improved uncertainty estimation
* Generative AI / LLM layer for decision support and natural-language explanations

⸻

Technologies Used

Programming & Data Science

* Python
* Pandas
* NumPy
* Scikit-learn
* SciPy
* Matplotlib
* Seaborn

Machine Learning

* Linear Regression
* Random Forest
* XGBoost

Explainable AI

* SHAP

Business Intelligence

* Microsoft Power BI

Statistical Analysis

* Correlation Analysis
* Hypothesis Testing
* Independent t-test
* ANOVA
* Cross Validation

⸻

Repository Structure

├── README.md
├── notebooks/
│   └── cardiac_cost_prediction.ipynb
│
├── data/
│   └── README.md
│
├── dashboard/
│   └── powerbi_dashboard.pbix
│
├── report/
│   └── business_report.pdf
│
└── images/
    ├── dashboard.png
    ├── shap_analysis.png
    └── model_comparison.png

⸻

Disclaimer

This project is presented for educational and portfolio purposes.

Any sensitive, confidential, proprietary, or patient-identifiable information should be removed before public distribution.

The model is a decision-support prototype and should not be used for clinical or financial decisions without appropriate validation, governance, monitoring, and domain-expert review.

⸻

Author

Mohamed

Data Science | Machine Learning | Generative AI & LLMs

Currently focused on building practical, end-to-end AI and Machine Learning solutions that connect technical modeling with real-world business problems.
