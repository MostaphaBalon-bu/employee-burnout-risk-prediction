# Employee Burnout Risk Prediction

!\[Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)
!\[Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.1+-orange?logo=scikit-learn)
!\[License](https://img.shields.io/badge/License-MIT-green)
!\[Status](https://img.shields.io/badge/Status-Complete-brightgreen)
!\[Course](https://img.shields.io/badge/Course-Data%20Mining-purple)

##  Project Overview

This project builds a \*\*machine learning classification system\*\* that predicts employee
burnout risk from anonymous workplace survey data. Using a dataset of 3,000 professionals,
we compare five classification algorithms, tune the best performer via GridSearchCV, and
translate model outputs into concrete business recommendations.

The project was completed in three milestones — EDA, data preparation, and model building
— culminating in a full final analysis with feature importance, ROI modeling, and a
deployment readiness assessment.

> \*\*Business case:\*\* Employee burnout costs U.S. organizations an estimated $190 billion
> annually in healthcare costs alone. This model enables targeted, proactive intervention
> that can save an organization of 3,000 employees approximately \*\*$3.6 million per year\*\*
> compared to no intervention strategy.

---

##  Objectives

- Identify the most significant predictors of employee burnout using survey data
- Build and compare five classification models on the same dataset
- Select and tune the best-performing model via GridSearchCV (5-fold cross-validation)
- Quantify the financial return on investment for deploying the model
- Provide a phased deployment roadmap with ethical safeguards

---

## 📊 Model Performance Summary

| Model | Cross-Val AUC | Test AUC | Precision | Recall | F1-Score |
|-------|:---:|:---:|:---:|:---:|:---:|
| \*\*Random Forest\*\*  | \*\*0.847 ± 0.021\*\* | \*\*0.851\*\* | \*\*0.82\*\* | \*\*0.78\*\* | \*\*0.80\*\* |
| Gradient Boosting | 0.839 ± 0.024 | 0.843 | 0.81 | 0.76 | 0.78 |
| Neural Network (MLP) | 0.828 ± 0.026 | 0.831 | 0.79 | 0.75 | 0.77 |
| Logistic Regression | 0.812 ± 0.019 | 0.818 | 0.78 | 0.73 | 0.75 |
| SVM | 0.805 ± 0.023 | 0.809 | 0.77 | 0.71 | 0.74 |

\*\*Winner: Random Forest\*\* with AUC = 0.851 after hyperparameter tuning
(`n\_estimators=200`, `max\_depth=20`, `min\_samples\_split=5`)

---

##  Top Burnout Risk Predictors

| Rank | Feature | Importance | Interpretation |
|------|---------|:---:|---|
| 1 | Stress Level | 18.2% | Primary psychological driver |
| 2 | Work-Life Balance Score | 15.7% | Most actionable workplace factor |
| 3 | Work Hours Per Week | 12.3% | Quantitative workload measure |
| 4 | Job Satisfaction | 9.8% | Overall job contentment |
| 5 | Manager Support Score | 8.5% | Leadership quality indicator |
| 6 | WorkHours × Stress Interaction | 7.2% | Compound workload-pressure effect |
| 7 | Commute Time | 6.8% | Daily stress contributor |
| 8 | Overall Wellbeing Score | 5.4% | Composite mental health indicator |
| 9 | Career Growth Score | 4.9% | Future opportunity perception |
| 10 | Mental Health Days Off | 3.7% | Behavioral health indicator |

---

##  Business Impact

| Scenario | Annual Cost (3,000 employees) |
|---|---|
| No intervention | $5.0 million |
| Random/blanket intervention | $3.5 million |
| \*\*Model-targeted intervention\*\* | \*\*$1.4 million\*\* |
| \*\*Savings vs. no intervention\*\* | \*\*$3.6 million\*\* |
| Per-employee savings | $1,200 |

- \*\*First-year ROI:\*\* 1,040% ($3.6M savings / $400K implementation cost)
- \*\*Ongoing annual ROI:\*\* 2,300% ($3.6M savings / $150K operating cost)
- \*\*Burnout incidence reduction:\*\* 40–60%

---

##  Dataset

- \*\*Source:\*\* \[Kaggle — Mental Health and Burnout in the Workplace](https://www.kaggle.com/)
- \*\*Records:\*\* 3,000 complete employee survey responses
- \*\*Features:\*\* 25 original + 9 engineered = 34 total features
- \*\*Target:\*\* `BurnoutRisk` — binary (0 = Low Risk, 1 = High Risk)
- \*\*Burnout prevalence:\*\* 42% of employees classified as high-risk
- \*\*Missing values:\*\* 0 (complete dataset)
- \*\*Framework:\*\* Maslach Burnout Inventory

---

##  Methods

### Milestone 1 — Exploratory Data Analysis
- Dataset validation: 3,000 records, 25 features, 0 missing values
- Correlation analysis (burnout vs. stress: r=0.72; vs. work-life balance: r=−0.68)
- Burnout risk by department: IT (51%), Support (48%), Sales (45%)
- Employees working 50+ hours/week showed 3.2× higher burnout risk
- Hybrid workers showed the highest burnout rate among remote work arrangements

### Milestone 2 — Data Preparation \& Feature Engineering
\*\*9 engineered features created:\*\*
- \*Interaction features:\* `WorkHours\_Stress\_Interaction`, `WorkLife\_Satisfaction\_Interaction`, `Commute\_WorkHours\_Interaction`
- \*Ratio features:\* `Stress\_Per\_WorkHour`, `MentalHealth\_Per\_Stress`
- \*Composite scores:\* `Overall\_Wellbeing\_Score`, `Support\_Score`
- \*Binned features:\* `Age\_Group`, `WorkHours\_Group`

\*\*Preprocessing pipeline:\*\*
- Stratified 80/20 train-test split (preserves class distribution)
- `StandardScaler` for numerical features
- `OneHotEncoder` for categorical variables
- `ColumnTransformer` for combined pipeline

### Milestone 3 — Model Building \& Selection
Trained and cross-validated five classifiers: Logistic Regression, KNN, SVM,
Random Forest, and Gradient Boosting. Models evaluated on AUC, F1, Precision, and Recall.

### Final Project — Tuning, Interpretation \& Deployment
- GridSearchCV with 5-fold CV on Random Forest
- Feature importance extraction and ranking
- ROI and cost-benefit financial modeling
- Phased deployment roadmap with ethical framework

---

##  Repository Structure

```
employee-burnout-risk-prediction/
├── notebooks/
│   ├── Milestone_1_2_3.ipynb          # EDA, data prep, and model building
│   └── Final_Project_Complete.ipynb   # Full analysis with tuning and ROI
├── data/
│   └── README_data.md                 # Dataset download instructions
├── reports/
│   └── Final_Project_Write.docx       # Written project report
├── images/                             # Exported chart images
├── requirements.txt
└── README.md
```

---

##  How to Run

```bash
# 1. Clone the repository
git clone https://github.com/YOUR-USERNAME/employee-burnout-risk-prediction.git
cd employee-burnout-risk-prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download the dataset (see data/README\_data.md)
# Save as: data/mental\_health\_workplace\_survey.csv

# 4. Run milestones in order
jupyter notebook notebooks/Milestone\_1\_2\_3.ipynb

# 5. Run the complete final analysis
jupyter notebook notebooks/Final\_Project\_Complete.ipynb
```
---
 Visualizations Produced
Burnout risk distribution (overall prevalence)
Burnout risk by work hours (binned bar chart)
Burnout risk by job satisfaction level
Burnout risk by remote work arrangement (on-site / hybrid / remote)
Burnout risk by department
Burnout risk by age group
Correlation heatmap of key numerical features
ROC curves for all five models
Model comparison bar chart (default vs. tuned Random Forest)
Top 10 feature importance chart (horizontal bar)
---
 Ethical Considerations
This model was built with the following safeguards in mind:
Risk	Mitigation
Algorithmic bias (age, gender, dept.)	Quarterly fairness audits across demographic groups
Mental health data privacy	Aggregated reporting only; no individual identification
Employee stigmatization	Results used for group-level insights, not individual labels
Over-reliance on model	Human HR review required for all high-risk classifications
Misuse as surveillance	Model positioned as diagnostic support, not performance evaluation
> \*\*Important:\*\* The model is \*\*not recommended for individual employee evaluation\*\*.
> It should be used as a \*\*diagnostic tool for teams and departments\*\* to guide
> supportive resource allocation.
---
 Deployment Roadmap
Phase 1: Foundation (Months 0–3)
Pilot deployment in one business unit (~500 employees)
Train HR staff and people managers on system interpretation
Develop 15+ intervention programs matched to risk profiles
Establish data governance and privacy protocols
Targets: 80% manager adoption, 90% employee awareness, <5% false positive rate
Phase 2: Organizational Scale (Months 3–12)
Full rollout with department-specific model calibration
Integrate predictions into existing HR systems via API
Monthly model retraining with new survey data
ROI tracking dashboard deployed
Targets: 40% reduction in burnout incidence, 25% decrease in burnout-related turnover
Phase 3: Strategic Evolution (Months 12+)
Shift focus from prediction to prevention via workplace redesign
Embed burnout prevention into leadership competency frameworks
Explore NLP on free-text survey responses
Develop prescriptive (recommendation) analytics layer
---
 Future Research Directions
Multimodal data: Email sentiment, calendar density, collaboration network analysis
Survival analysis: Predict when burnout will occur, not just if
Causal inference: Move beyond correlation to establish causal intervention effects
NLP integration: Analyze free-text survey fields for nuanced sentiment signals
Longitudinal modeling: Track burnout risk evolution over time for individual employees
---
 License
This project is licensed under the MIT License.
---
 Acknowledgements
Dataset: Kaggle — Mental Health and Burnout in the Workplace
Burnout framework: Maslach, C., & Leiter, M.P. Maslach Burnout Inventory
Business statistics: World Health Organization (2024), Gallup (2023), Harvard Business Review (2024)


---

