# Credit Risk Analysis Report

## Overview of the Analysis  
We developed a logistic regression model to predict whether a loan is **healthy** (0) or **high-risk** (1) using a peer-to-peer lending dataset. After loading the data and inspecting its features, we:

1. Split the `loan_status` column into labels (`y`) and the remaining columns into features (`X`).  
2. Performed a 70/30 train/test split.  
3. Trained a `LogisticRegression` model on the training set.  
4. Generated predictions on the test set and evaluated performance using a confusion matrix and classification report.  

## Results  
- **Accuracy:** 0.99  
- **Precision (healthy loans, 0):** 1.00  
- **Precision (high-risk loans, 1):** 0.85  
- **Recall (healthy loans, 0):** 0.99  
- **Recall (high-risk loans, 1):** 0.95  

*(Support: 18 759 healthy; 625 high-risk; total test samples: 19 384.)*  

## Summary and Recommendation  
The model achieves very high overall accuracy (0.99), correctly identifying nearly all healthy loans. It also captures 95% of actual high-risk loans (recall = 0.95), though about 15% of predicted high-risk loans are false positives (precision = 0.85).  

Because missing a high-risk loan (false negative) carries greater financial risk than occasionally flagging a healthy loan, the strong recall for class 1 makes this model suitable for deployment. If further reduction of false positives is desired, consider tuning the classification threshold or exploring ensemble methods (e.g., Random Forest) to improve the precision–recall balance.  

---

*Note: This report will be included in the project README under “Credit Risk Analysis.”*