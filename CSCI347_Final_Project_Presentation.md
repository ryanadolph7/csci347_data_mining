# CSCI 347 Final Project Presentation
## Predicting Credit Card Default Risk Using Classification Models

Target length: 12 minutes  
Recommended length: 11 slides  
Pacing: about 60-75 seconds per content slide

---

## Slide 1: Title

**Layout:** Title slide

**On slide:**
- Predicting Credit Card Default Risk Using Classification Models
- CSCI 347 Data Mining Final Project
- Ryan Adolph, Braeden Olds, Michael Oswald
- Dataset: UCI Default of Credit Card Clients

**Speaker notes:**
Introduce the project as a supervised binary classification problem. The goal is to predict whether a credit card client will default on their payment the following month.

**Time:** 30 seconds

---

## Slide 2: Problem and Goal

**Layout:** Two-column slide

**Left side: Problem**
- Credit card companies need to estimate default risk.
- The prediction target is binary:
  - 0 = no default
  - 1 = default

**Right side: Project goal**
- Build an end-to-end data mining pipeline.
- Compare several classification models.
- Use stratified k-fold cross-validation.
- Identify important predictors of default risk.

**Speaker notes:**
Explain that this is not only about getting a high accuracy score. Since default prediction has real financial and customer impacts, the project also compares models using recall, F1-score, and ROC-AUC.

**Time:** 1 minute

---

## Slide 3: Stakeholders and Value

**Layout:** Three-card layout

**Cards:**
- **Banks and credit card companies:** identify higher-risk accounts
- **Financial analysts and risk teams:** understand patterns linked to default
- **Customers:** may be affected by account reviews, reminders, or credit decisions

**Bottom note:**
Credit risk prediction has value, but also fairness and ethical concerns.

**Speaker notes:**
Emphasize that this model could support decision-making, but should not replace human review. Demographic features and false predictions can create fairness problems in real-world credit decisions.

**Time:** 1 minute

---

## Slide 4: Dataset Overview

**Layout:** Table plus short description

**Table:**

| Item | Value |
|---|---:|
| Dataset | Default of Credit Card Clients |
| Source | UCI Machine Learning Repository |
| Instances | 30,000 |
| Input features | 23 |
| Target | Default payment next month |
| Task | Binary classification |

**Feature groups:**
- Credit limit
- Demographics
- Payment history
- Bill statement amounts
- Previous payment amounts

**Speaker notes:**
Briefly explain that the dataset contains credit card clients from Taiwan and includes both financial behavior variables and demographic variables. The target column indicates whether the client defaulted next month.

**Time:** 1 minute

---

## Slide 5: Data Inspection and Class Balance

**Layout:** Chart-focused slide

**Visual to use:**
- Class balance bar chart from the notebook

**Key points:**
- Non-default clients are the majority class.
- Default clients are the minority class.
- Accuracy alone can be misleading.

**Speaker notes:**
Explain that class imbalance affects evaluation. A model can get high accuracy by mostly predicting no default, so the project also uses precision, recall, F1-score, and ROC-AUC.

**Time:** 1 minute

---

## Slide 6: Exploratory Data Analysis

**Layout:** 2x2 visual grid

**Visuals to use:**
- Age distribution histogram
- Credit limit histogram
- Correlation heatmap
- Payment history comparison by default status

**Key takeaways:**
- Many clients are concentrated in younger-to-middle adult age ranges.
- Credit limits are right-skewed.
- Bill amount variables are correlated with each other.
- Recent payment status differs between default and non-default clients.

**Speaker notes:**
Focus on the payment history chart as the most important EDA finding. Clients who defaulted tended to have worse recent repayment status, which suggests payment history will be useful for prediction.

**Time:** 1.5 minutes

---

## Slide 7: Preprocessing Pipeline

**Layout:** Flow diagram

**Flow:**
Raw data -> Feature groups -> Preprocessing -> Model training -> Evaluation

**Preprocessing choices:**
- `SEX`, `EDUCATION`, and `MARRIAGE` were one-hot encoded.
- Numeric features were median-imputed.
- Logistic Regression and KNN used scaled numeric features.
- Tree-based models used unscaled numeric features.
- Pipelines were used so preprocessing happened inside cross-validation.

**Speaker notes:**
Explain why categorical codes should not be treated as normal numeric values. Also explain why scaling matters for models like Logistic Regression and KNN, but not for tree-based models.

**Time:** 1 minute

---

## Slide 8: Models Compared

**Layout:** Model comparison list

**Models:**
- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbors
- Gradient Boosting

**Evaluation setup:**
- Stratified 5-fold cross-validation
- Fixed random seed
- Metrics: accuracy, precision, recall, F1-score, ROC-AUC

**Speaker notes:**
Mention that Logistic Regression served as a simple baseline. Decision Tree and Random Forest added nonlinear models. KNN provided a distance-based comparison. Gradient Boosting was included as a stronger advanced model for tabular data.

**Time:** 1 minute

---

## Slide 9: Cross-Validation Results

**Layout:** Results table with highlighted winner

**Table to use from notebook:** `comparison_table`

**Main results:**
- Gradient Boosting had the best overall balance.
- Gradient Boosting:
  - Accuracy: about 0.821
  - F1-score: about 0.474
  - ROC-AUC: about 0.781
- Decision Tree had the highest recall, but weaker overall performance.

**Speaker notes:**
Explain the tradeoff. Decision Tree found more default cases but made more mistakes overall. Gradient Boosting had the best combination of F1-score and ROC-AUC, so it was chosen as the final model.

**Time:** 1.5 minutes

---

## Slide 10: Final Model and Feature Importance

**Layout:** Split slide

**Left side: Holdout test results**
- Final model: Gradient Boosting
- Accuracy: about 0.82
- ROC-AUC: about 0.780
- Default-class precision: about 0.66
- Default-class recall: about 0.36
- Default-class F1-score: about 0.47

**Right side: Feature importance chart**
- Use top 20 feature importance chart from notebook.

**Key feature takeaway:**
Recent payment history was the strongest predictor, especially payment status in the most recent month.

**Speaker notes:**
Explain that the final model performed well overall but still struggled with recall for the default class. This means it missed some actual defaults. The feature importance results make practical sense because recent payment delays are closely connected to future default risk.

**Time:** 1.5 minutes

---

## Slide 11: Conclusion and Future Work

**Layout:** Two-column slide

**Left side: Conclusion**
- Gradient Boosting was the best final model.
- Recent repayment status was the strongest signal.
- The model could support risk review and early warning processes.
- It should not be the only basis for credit decisions.

**Right side: Future work**
- Threshold tuning to improve recall
- Hyperparameter tuning
- Fairness analysis across demographic groups
- Cost-sensitive learning
- Test XGBoost, LightGBM, or neural networks
- Model calibration for better risk probabilities

**Speaker notes:**
Close by connecting the model back to the stakeholders. The project shows that data mining can identify useful risk patterns, but real-world deployment would need stronger fairness checks, better recall, and careful treatment of false positives and false negatives.

**Time:** 1 minute

---

## Timing Summary

| Slide | Topic | Time |
|---:|---|---:|
| 1 | Title | 0:30 |
| 2 | Problem and goal | 1:00 |
| 3 | Stakeholders | 1:00 |
| 4 | Dataset | 1:00 |
| 5 | Class balance | 1:00 |
| 6 | EDA | 1:30 |
| 7 | Preprocessing | 1:00 |
| 8 | Models and evaluation | 1:00 |
| 9 | Cross-validation results | 1:30 |
| 10 | Final model and feature importance | 1:30 |
| 11 | Conclusion and future work | 1:00 |
| **Total** |  | **12:00** |

