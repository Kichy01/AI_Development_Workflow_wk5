Model Development (8 Points)
Chosen Model & Justification
Selected Model: Random Forest Classifier


Justification:

A Random Forest is selected due to its ability to handle structured student data effectively. It consists of multiple decision trees and uses majority voting to improve prediction reliability. This model is suitable for predicting dropout risk because:
- It handles both numerical and categorical features effectively.
- It is resistant to noise and missing values, common in student academic datasets.
- It reduces overfitting by averaging multiple trees.
- It allows interpretation of feature importance (e.g., attendance, grades, participation).
- It offers a good balance between accuracy, performance, and interpretability compared to deep neural networks.

This model supports educational analytics where transparency and fairness are essential.
Data Splitting Strategy

Dataset Split:
- 70% Training Set – Used to learn and build the Random Forest model.
- 15% Validation Set – Used for model tuning and improving performance.
- 15% Test Set – Used to evaluate final model performance on unseen data.

A stratified sampling approach will be applied to ensure proportional representation of dropout vs. non-dropout students in each dataset, reducing class imbalance risk and ensuring fair evaluation.
Hyperparameters to Tune & Why

Two key hyperparameters to tune:
1. n_estimators (Number of Trees)
   - Controls the number of decision trees used in the model.
   - Higher values improve accuracy but increase training time.
   - Tuning helps balance accuracy and computational cost.

2. max_depth (Maximum Tree Depth)
   - Limits how deep each decision tree can grow.
   - Prevents overfitting by controlling model complexity.
   - Enhances generalization to new unseen data.
   
Additional tuning methods such as Grid Search or Random Search with cross‑validation will be used to identify optimal hyperparameter settings.
