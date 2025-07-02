# credit_risk_hybrid_model
<br/>
Objective:<br/>
● Develop and validate a hybrid model integrating qualitative and quantitative indicators to improve the prediction of default probability.
<be/>
Models were trained using only quantitative financial indicators. Performance was evaluated using standard classification metrics on a hold-out test set and cross-validation.<br/>



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
