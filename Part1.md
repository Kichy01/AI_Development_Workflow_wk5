Part 1: Short Answer Questions Assignment(30 points)
1.Problem Definition (6 points)
a) AI Problem:
Online learning Student dropout prediction.
The idea is to forecast using AI the probability that a student is on the brink of leaving school before the semester is over so that the academic support personnel can intervene in time.

b)
i) Objectives (3):
Early Identification: To identify students who are likely to drop out, this is done at least four weeks before the end of the term so that interventions can be done with these students.
Precision and Performance: A true positive rate (recall) of 75 of identifying at-risk students with a false positive of less than 25.
Interpretability: Explain the interpretation of every prediction in a way that makes sense to the staff using interpretable AI procedures to ensure that the staff is able to trust the results.

ii) Stakeholders (2):
Students: They are the immediate beneficiaries of the personalized intervention and better academic performance.
Academic Advisors/Counselors: These individuals utilize the output of AI to focus on outreach and manage the resource distribution.

c) Key Performance Indicator (KPI):
Intervention-Adjusted Retention Lift: The percentage of student retention increase in the group of students identified as a high risk and reinforced with intervention in comparison to a control group.
And (this KPI directly quantifies the improvement in retention caused by the model)

2.Data Collection, Data Preprocessing (8 points)
a) Data Sources (2):
Instructors: This feature allows an educator to browse all Learning Management System (LMS) logs. This option enables an instructor to view all Learning Management System (LMS) logs.
Where login frequency, page view, submissions in assignments and in discussion forums, time spent and session durations are included.
Student Information System:
Presents the demographic information (age, enrollment status), academic performance (GPA, credit hours), and financial or registration information.

b) Potential Bias in the Data (1):
Bias in selection and socioeconomic Confounding:
Low-socioeconomic-students may lack good internet connection and therefore do not seem to be active in LMS data and the model can falsely link low engagement with dropout information based on lack of internet connection and not motivation or ability.

c) Preprocessing Steps (3):
Handling Missing Data:
Where there are missing numeric values replace them with median values or zeroes.
Missing categorical fields are used as unknown categories.
Add indicator variables on the fields that have been imputed to indicate the point of missingness.
Normalization and Feature Engineering:
Continuous data (e.g. number of logins, time spent) using robust scaling to minimize the effect of outliers.
Additional features such as average assignment delay, weekly active hours or forum participation rate can be created.

Alignment of Temporal and Creation of Labels:

Align (e.g., use weeks 1-8 to predict dropout by week 12).

Time-based cross-validation should be used to avoid data leakage amongst semesters or student groups.

3. Model Development (8 points)
a) Chosen Model:
The Gradient Boosted Decision Trees (XGBoost or LightGBM)

b)
i)  Justification:
Works very fast on structured/tabular data.
Is able to do nonlinear interactions of features with minimal preprocessing.
Supports interpretability by offers that are built-in with in-built feature importance and SHAP (SHapley Additive exPlanations).

ii) Data Splitting:
In a bid to prevent overfitting and be fair:
Training Set: 60 percent of first term student data.
The validation set: Hyperparameter tuning and model selection: Next 20%.
Test Set: Final 20% to be able to assess performance objectively.
Group on the basis of student ID so that no data of the same student is included in more than one set.

c) Hyperparameters to Tune (2):
Learning Rate (e):
Regulates the rate at which the model varies with boosting iteration. Reduced learning rates using more trees tend to generalize.
Max Tree Depth (max_depth):
Defines the complexity of the decision trees that the model should have. To avoid over-fitting, it can be balanced by tuning.

4. Most importantly, evaluation and deployment (8 points)
a) Evaluation Metrics (2):
Area Under Precision-Recall Curve (AUPRC):
More suitable with skewed datasets in which dropouts are a minority group. Concentrates on the number of at-risk students who get identified properly.

Fixed Precision Recall (e.g., 80% Precision): Measures the number of true positives we pick up on when we restrict interventions to high-confidence predictions (e.g. 80 percent precision). This regulates the distribution of resources and prevents false alarms.

b) Concept Drift:
Definition: Concept drift is a situation where the correlation between the input features (e.g., activity levels) and the target variable (dropout) varies with time.
Scenario: There is a shift in the behavior of students due to a new learning platform or grading system, rendering previous models ineffective.

How to Monitor Concept Drift:
The tracking of the distribution of features:
Compare statistical values of features (means, standard deviations) between periods with the aid of such tools as Population Stability Index (PSI).

Performance Monitoring:
Measures of track (AUPRC, Recall) on new batches of data. In case the performance declines sharply, explore retraining.

Automated Alerts:
Trigger retraining in case of PSI greater than 0.2 or AUPRC decreases more than 10%. A periodically updating model is required.

c) Technical Issue in the Deployment:
Real-Time Predictions and Explanations: Scalability:
Real-time systems can be slowed down by generating SHAP explanations of every prediction.

Solutions:
ApOD Use approximate SHAP methods that are optimized on tree based models.
Precomputing common cases or asynchronous computation of common cases.
Run the model on a containerized back-end (e.g., Docker + Kubernetes) that is auto-scaling and batch inference to scale throughput.

Ethical & Pragmatic Intuitions (Critical Analysis).
Privacy and Data Protection:
Delete personally identifiable information and data protection laws.
Apply such methods as feature hashing or differential privacy.
Equality and Prejudice Reduction:
On a periodic basis, review model outputs as demographic subgroups (gender, age, SES).
Train or retrain the model in case there is performance variance.
Human-in-the-Loop Approach:
Engage academic personnel in decision making.
Explain (why a student is high-risk) instead of just labels of risks.

Pragmatical Deployment Reflections:
Watch label delays (true dropout labels can only be determined out of term).
The use of controlled experiments as the means of test interventions to make them enhance retention, not just correlate with it.

Limitations:
It is risk, rather than causation that is projected through the model.
Students with low digital connectivity may be under-categorized as high-risk since there was no LMS data.

References
Ribeiro, M. T., Singh, S., & Guestrin, C. (2016). "Why Should I Trust You?": Prediction of any Classifier. ACM SIGKDD.
Molnar, C. (2020). Explainable Artificial Intelligence.
Widmer, G., & Kubat, M. (1996). Learning under Concept drift and Hidden contexts. Machine Learning.
Biecek, P., & Burzykowski, T. (2021). Explanatory Model Analysis.
