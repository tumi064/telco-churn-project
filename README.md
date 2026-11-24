# Predicting Customer Churn in Telecommunications

## Project overview
This group project uses the IBM/Kaggle Telco Customer Churn dataset to explore customer churn and compare machine-learning classifiers that predict whether a customer will leave the service.

**Research question:** Which customers are most likely to leave, and what patterns are associated with churn?

## Project workflow
1. **Data cleaning** — inspect the original dataset, convert `TotalCharges` to numeric, remove 11 rows with missing `TotalCharges`, drop the customer identifier, and encode `Churn` as 1 (Yes) and 0 (No).
2. **Exploratory analysis** — examine churn patterns across contract type, tenure, monthly charges, payment method and internet service.
3. **Modelling** — one-hot encode categorical predictors; use a stratified 80/20 train/test split; train Logistic Regression, Decision Tree and Random Forest classifiers.
4. **Evaluation** — compare churn-class precision, recall and F1-score, alongside overall accuracy; inspect feature importance and logistic-regression coefficients.
5. **Recommendations** — identify customer groups for targeted retention actions.

## Dataset
- Original records: 7,043
- Records after cleaning: 7,032
- Original columns: 21
- Cleaned columns: 20
- Encoded model predictors: 30
- Churn rate: approximately 26.6%

The dataset is the Telco Customer Churn dataset, originally released by IBM and commonly distributed via Kaggle. The analysis describes associations in this dataset and does not establish causation.

## Model results
Results below are from the held-out test set (1,407 customers; 374 churners).

| Model | Churn precision | Churn recall | Churn F1 | Accuracy |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.491 | **0.797** | **0.608** | 0.726 |
| Decision Tree | 0.468 | 0.783 | 0.586 | 0.706 |
| Random Forest | **0.560** | 0.660 | 0.606 | **0.772** |

Logistic Regression is recommended when the priority is to identify as many churners as possible (highest recall: 0.797; 298 of 374 churners detected). Random Forest has the highest precision and overall accuracy, and may be preferable when retention-offer costs make false alarms more expensive. The best model therefore depends on the business objective.

## Key findings and recommendations
- Month-to-month customers have a 42.7% churn rate; consider incentives for longer-term contracts.
- Customers in their first 12 months have a 47.7% churn rate; strengthen onboarding and early support.
- Fiber-optic customers have a 41.9% churn rate; investigate service quality, pricing and competitor offers.
- Electronic-check users have a 45.3% churn rate; test incentives for switching to automatic payment.

These are observed associations, not proof that the listed factors cause churn. Retention actions should be tested before broad deployment.

## Repository contents
- `01_cleaning.ipynb` — data inspection and cleaning
- `02_exploration.ipynb` — exploratory data analysis (filename currently uses the letter O)
- `03_modelling.ipynb` — model training and prediction export
- `04_evaluation.ipynb` — model comparison, feature interpretation and recommendations
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` — original dataset
- `telco_clean.csv` — cleaned dataset
- `test_predictions.csv` — held-out test predictions
- `log_model.pkl`, `tree_model.pkl`, `rf_model.pkl` — saved fitted models
- `feature_importance_lr.png`, `feature_importance_rf.png` — model interpretation plots
- `Predicting_Customer_Churn_2_Pages.docx` — two-page project report
- `Churn_Project_Presentation_FINAL.pptx` — final group presentation

## How to reproduce
The notebooks are intended to be run in order:
1. Open `01_cleaning.ipynb` and run all cells.
2. Open `02_exploration.ipynb` and run all cells.
3. Open `03_modelling.ipynb` and run all cells.
4. Open `04_evaluation.ipynb` and run all cells.

Use a Python environment with pandas, numpy, matplotlib, scikit-learn and joblib installed. Run notebooks from the repository root so the relative data paths resolve.

## Group
Introduction to Data Science — Group E.
