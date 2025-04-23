# Credit Risk Classification Notebook  
**Module 20 – Supervised Machine Learning**  
**EdX/UT Data Analytics and Visualization Bootcamp**  
**Cohort UTA-VIRT-DATA-PT-11-2024-U-LOLC**  
**Author:** Neel Agarwal  

---

## Table of Contents  
1. [Project Overview](#project-overview)  
2. [Installation & Setup](#installation--setup)  
3. [Notebook Contents](#notebook-contents)  
4. [Data Description](#data-description)  
5. [Modeling Process](#modeling-process)  
6. [Results](#results)  
7. [Recommendations](#recommendations)  
8. [Directory Structure](#directory-structure)  
9. [Running the Notebook](#running-the-notebook)  
10. [References & Citations](#references--citations)  

---

## Project Overview  
This Jupyter Notebook implements a **logistic regression** model to classify peer-to-peer loans as **healthy** (0) or **high-risk** (1). We perform a 70/30 train/test split, fit the model, and evaluate performance via precision, recall, and accuracy.

---

## Installation & Setup  
1. **Clone the repository**  
   ```bash
   git clone https://github.com/yourusername/CreditRiskClassification.git
   cd CreditRiskClassification
   ```  
2. **Create & activate a virtual environment** (recommended)  
   ```bash
   python3 -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```  
3. **Install required packages**  
   ```bash
   pip install pandas scikit-learn jupyter
   ```

---

## Notebook Contents  
The `credit_risk_classification.ipynb` is organized into these main sections:  
- **Cell 1:** Imports & configuration  
- **Cell 2:** Data loading & exploration  
- **Cell 3:** Train/Test split  
- **Cell 4:** Model training (LogisticRegression)  
- **Cell 5:** Predictions & evaluation (confusion matrix, classification report)  
- **Cell 6:** Discussion & interpretation  

---

## Data Description  
- **File:** `Resources/lending_data.csv`  
- **Features:** Borrower income, debt ratio, credit history length, etc.  
- **Target:** `loan_status` (0 = healthy, 1 = high-risk)

---

## Modeling Process  
1. **Read data** into a Pandas DataFrame.  
2. **Define X & y:**  
   ```python
   X = lending_df.drop(columns=["loan_status"])
   y = lending_df["loan_status"]
   ```  
3. **Split:**  
   ```python
   from sklearn.model_selection import train_test_split
   X_train, X_test, y_train, y_test = \
       train_test_split(X, y, random_state=42)
   ```  
4. **Train:**  
   ```python
   from sklearn.linear_model import LogisticRegression
   model = LogisticRegression(max_iter=1000)
   model.fit(X_train, y_train)
   ```  
5. **Evaluate:**  
   ```python
   from sklearn.metrics import classification_report
   preds = model.predict(X_test)
   print(classification_report(y_test, preds))
   ```

---

## Results  
- **Accuracy:** 0.99  
- **Precision:**  
  - Class 0 (healthy): 1.00  
  - Class 1 (high-risk): 0.85  
- **Recall:**  
  - Class 0 (healthy): 0.99  
  - Class 1 (high-risk): 0.95  

_Total test samples: 19 384 (18 759 healthy; 625 high-risk)._

---

## Recommendations  
- **Deploy** the logistic model as-is: high recall on high-risk loans ensures few defaults slip through.  
- To **reduce false positives**, consider:  
  - Adjusting the decision threshold  
  - Testing ensemble methods (e.g., Random Forest) for better precision–recall trade-off

---

## Directory Structure  
```plaintext
CreditRiskClassification/
├── Credit_Risk/
│   ├── credit_risk_classification.ipynb
│   └── Resources/
│       └── lending_data.csv
├── analysis_report.md
└── README.md
```

---

## Running the Notebook  
1. Activate your environment:  
   ```bash
   source venv/bin/activate
   ```  
2. Launch Jupyter:  
   ```bash
   jupyter notebook
   ```  
3. Open **credit_risk_classification.ipynb**, run all cells in order, and observe outputs.

---

## References & Citations  
1. **scikit-learn LogisticRegression & Metrics**  
   – https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression  
   – https://scikit-learn.org/stable/modules/model_evaluation.html#classification-metrics  
2. **pandas Documentation**  
   – https://pandas.pydata.org/docs/  
3. **Module 20 Rubric** (provided by EdX/2U Bootcamp)  
4. **Dataset Source:** `lending_data.csv` from Module 20 assignment  
5. **README style inspired by** previous Bootcamp projects and ChatGPT assistance  
---