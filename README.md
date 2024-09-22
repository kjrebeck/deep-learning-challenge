
# **Neural Network for Predicting Charity Funding Success: Alphabet Soup Case Study**

## **Project Overview**

Alphabet Soup, a nonprofit foundation, is seeking a machine learning tool to help predict which applicants for funding are most likely to be successful. This project uses historical data from over 34,000 organizations to build a binary classifier that predicts whether an applicant will successfully use the funding. The goal is to provide insights to help Alphabet Soup make informed decisions about funding allocations.

## **Data Preprocessing**

Key steps in data cleaning and feature engineering included:

- **Target Variable**: `IS_SUCCESSFUL` (1 = successful use of funds, 0 = not successful).
- **Features Used**: 
  - `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`
  - Binned `INCOME_AMT` into three categories (None, Middle, High)
  - Created new binary features:
    - `OVER_5000`: Indicates whether the requested amount exceeds \$5,000.
    - `FOR_PROFIT`: Indicates if the organization is for-profit (yes/no).
    - `NAME_CATEGORY`: Categorized organizations based on common words in their names (e.g., "CLUB," "FOUNDATION," "VETERAN").

## **Model Development**

### **Initial Model**
- Two hidden layers:
  - Layer 1: 100 neurons (ReLU activation)
  - Output Layer: 1 neuron (Sigmoid activation)
- **Accuracy**: ~72.82%
- **Loss**: 0.5585

### **Optimized Model**
- Three hidden layers with batch normalization:
  - Layer 1: 100 neurons (ReLU) + Batch Normalization
  - Layer 2: 50 neurons (ReLU) + Batch Normalization
  - Layer 3: 25 neurons (ReLU) + Batch Normalization
  - Output Layer: 1 neuron (Sigmoid)
- **Accuracy**: ~76.42%
- **Loss**: 0.5131

## **Results**

The optimized model outperformed the initial model, achieving an accuracy of **76.42%**. Feature engineering, batch normalization, and hyperparameter tuning contributed to the improvements in model performance.

## **Future Work**

While the deep learning model performed well, further improvements could be made using alternative models such as **Random Forest** or **XGBoost** to better handle categorical features and enhance interpretability.

## **Work Cited**

1. IRS. Tax Exempt Organization Search Bulk Data Downloads. https://www.irs.gov/Links to an external site.
2. CHATGBT

---
