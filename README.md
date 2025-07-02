# credit_risk_hybrid_model
<br/>
Objective:<br/>
● Develop and validate a hybrid model integrating qualitative and quantitative indicators to improve the prediction of default probability.
<be/>
Models were trained using only quantitative financial indicators. Performance was evaluated using standard classification metrics on a hold-out test set and cross-validation. To assess the probability of default, several classification models were trained and compared. Both linear and non-linear approaches were applied to evaluate performance, interpretability, and operational suitability for banking environments.<br/>

Key Objectives of Model Benchmarking:<br/>
● Evaluate predictive power (AUC, F1-score, precision, recall)<br/>
● Assess calibration quality (Brier Score)<br/>
● Compare interpretability vs complexity<br/>
● Test impact of integrating qualitative variables.<br/>


## 1st stage<br/>
Model Comparison (quantitative factors only)<br/>

Performance Comparison Table 1
| Model               |  AUC      | Brier Score | Accuracy | precision | recall | f1-score | 
|---------------------|-----------|-------------|----------|-----------|--------|----------|
| Logistic Regression | 0.908125  | 0.125271    | 0.8375   | 0.813953  | 0.875  | 0.843373 |        
| Random Forest       | 0.88125   | 0.141613    | 0.7875   | 0.755556  | 0.85   | 0.8      |
| Gradient Boosting   | 0.896875  | 0.147641    | 0.7875   | 0.780488  | 0.8    | 0.790123 |
| SVM                 | 0.891875  | 0.145791    | 0.8125   | 0.765957  | 0.9    | 0.827586 |


● Logistic Regression achieved the highest AUC and F1 Score, confirming strong overall performance.<br/>
● SVM showed the best recall (90%), making it effective in detecting defaults but at the cost of precision.<br/>
● Logistic Regression offers the best balance between accuracy, interpretability, and regulatory suitability.<br/>


## 2nd stage<br/>
Model Performance After Integrating Qualitative Factors
<br/>
To test the effect of qualitative indicators (litigation, audit status, external rating), all models were retrained using both financial and non-financial data. Performance metrics improved across all models, confirming the value of hybrid modeling.
<br/>
Performance Comparison Table 2
| Model               |  AUC      | Brier Score | Accuracy | precision | recall | f1-score | 
|---------------------|-----------|-------------|----------|-----------|--------|----------|
| Logistic Regression | 0.914375  | 0.115571    | 0.825    | 0.809524  | 0.85   | 0.829268 |        
| Random Forest       | 0.902187  | 0.129993    | 0.7875   | 0.744681  | 0.875  | 0.804598 |
| Gradient Boosting   | 0.93      | 0.112071    | 0.825    | 0.809524  | 0.85   | 0.829268 |
| SVM                 | 0.91375   | 0.126512    | 0.8125   | 0.777778  | 0.875  | 0.823529 |

● Gradient Boosting achieved the best AUC and calibration.<br/>
● Logistic Regression matched Gradient Boosting in F1 Score and maintained superior interpretability.<br/>
● SVM delivered the highest recall, which is critical for default detection.<br/>
● Qualitative features significantly improved all models' ability to discriminate and calibrate default risk.


## 3rd stage<br/>
Final Model Training and 5-fold Cross-Validation and Results<br/>
The final logistic regression model, incorporating both quantitative and qualitative features, was trained using L2 regularization and evaluated through stratified 5-fold cross-validation to ensure 
robustness and generalizability.

Test Set Performance:
| Metric      |  Value  |  
|-------------|---------|
| AUC         | 0.9144  |      
| Brier Score | 0.1156  | 
| Accuracy    | 0.8250  | 
| Precision   | 0.8095  | 
| Recall      | 0.8500  |
| F1-score    | 0.8293  |

The model shows strong discrimination and calibration on unseen data, confirming its suitability for practical credit risk assessment in banking. <br/>
<br/>
The confusion matrix provides a detailed view of classification performance on the test set, showing how well the model distinguishes between defaulted and non-defaulted borrowers. <br/>
|        |       | Predicted | Predicted |  
|--------|-------|-----------|-----------|
|        |       | No        |  Yes      |
| Actual | No    | 32        | 8         |
| Actual | Yes   | 6         | 34        | 

● True Positives (TP = 34): Defaulted borrowers correctly identified.<br/>
● True Negatives (TN = 32): Non-defaulted borrowers correctly identified.<br/>
● False Positives (FP = 8): Non-defaulters wrongly classified as defaulters.<br/>
● False Negatives (FN = 6): Missed defaulters — potentially high-risk.<br/>
<br/>
Model Strengths: <br/>
● High recall (85%) indicates strong ability to detect true defaulters.<br/>
● Balanced precision and F1-score reflect overall stable performance.<br/>
● Low number of false negatives is important for minimizing unexpected credit losses.<br/>
