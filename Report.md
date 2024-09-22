# **Neural Network for Predicting Charity Funding Success: Alphabet Soup Case Study**

## **Introduction**

Alphabet Soup, a nonprofit foundation, seeks a tool to predict which applicants for funding are most likely to succeed in their ventures. To support this, a machine learning model has been developed using historical data from over 34,000 organizations. This project aims to create a binary classifier that can determine whether an applicant will effectively use the funds, helping Alphabet Soup allocate its resources more wisely. This report will cover two iterations of the model development process: an initial model and an optimized version that incorporates advanced data cleaning, feature engineering, and tuning.

---

## **Data Preprocessing**

In the first notebook, the target variable for the model was defined as `IS_SUCCESSFUL`, which indicates whether the organization successfully used the funding provided by Alphabet Soup. The features used in the initial model included key variables such as `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, and `ASK_AMT`, which represented the amount of funding requested.

For data cleaning, non-predictive variables, such as `EIN` and `NAME`, were removed from the dataset. These were identification columns that did not contribute to the model's ability to predict success.

In the second notebook, a more refined data preprocessing approach was applied. The `INCOME_AMT` feature was binned into categories, with ranges defined as:
- **None**: \$0
- **Middle**: \$1 to \$999,999
- **High**: Over \$1M

Additionally, the `ASK_AMT` variable was replaced with a new binary feature, `OVER_5000`, which indicated whether the requested amount exceeded \$5,000. A new binary feature, `FOR_PROFIT`, was created to indicate whether the organization had a positive income (yes/no).

Another important step in the second notebook was the grouping of organization names using regular expressions (regex). The `NAME` column was analyzed for common patterns, and based on these patterns, a new feature called `NAME_CATEGORY` was created. This feature grouped organizations into various categories, such as "CLUB/ORGANIZATION," "FOUNDATION/TRUST," "VETERAN/MILITARY," and others, based on keywords found in their names.

---

## **Model Compilation, Training, and Evaluation**

### **Initial Model (First Notebook)**

The initial model architecture was relatively simple, consisting of two hidden layers. The first hidden layer contained 100 neurons and used the ReLU activation function, while the second layer was the output layer with 1 neuron using the Sigmoid activation function, appropriate for binary classification tasks. 

During training, this model achieved an accuracy of approximately **72.82%** on the validation set, with a loss of **0.5585**. While the initial results were promising, the model’s performance left room for improvement, especially in its ability to generalize and predict outcomes more accurately.

### **Optimized Model (Second Notebook)**

In the second iteration, the model was optimized through several key techniques, including regularization, batch normalization, and hyperparameter tuning. Two versions of the optimized model were developed:

#### **Model 2A**
This model consisted of three hidden layers with 100, 75, and 25 neurons, respectively, using the ReLU activation function for each layer. The final output layer again used the Sigmoid function. 

Model 2A achieved an accuracy of **76.26%** and a loss of **0.5323** on the validation set. This was an improvement over the initial model, reflecting the value of a deeper network architecture.

#### **Model 2B**
Model 2B introduced **batch normalization** and **dropout** layers to improve training stability and reduce overfitting. It also used the Leaky ReLU activation function to address the issue of "dying neurons" that can occur with traditional ReLU.

This model consisted of:
- A first hidden layer with 100 neurons followed by batch normalization.
- A second hidden layer with 50 neurons and batch normalization.
- A third hidden layer with 25 neurons and batch normalization.
- The output layer with 1 neuron using the Sigmoid activation function.

Model 2B outperformed the previous iterations, achieving an accuracy of **76.42%** and a loss of **0.5131**. These improvements were primarily due to the introduction of regularization techniques and hyperparameter tuning.

---

## **Steps to Improve Model Performance**

Several steps were taken in the second notebook to improve the model’s performance:

1. **Regularization**: Dropout layers were introduced to randomly deactivate a fraction of neurons during training, which helped prevent overfitting and improve the generalization ability of the model.
  
2. **Batch Normalization**: This was used after each hidden layer to standardize the inputs to the layers, allowing the model to train more effectively and converge faster.
  
3. **Leaky ReLU Activation**: This activation function was chosen over the standard ReLU to prevent the "dying neurons" issue, where neurons become inactive during training.
  
4. **Hyperparameter Tuning**: Using the Keras Tuner, several hyperparameters were optimized, including the number of neurons in each layer, the learning rate, and the dropout rate. The tuning process led to an optimal configuration, reflected in the improved model performance.

---

## **Summary of Results**

The initial model, while effective, achieved an accuracy of **72.82%** with a loss of **0.5585**. By optimizing the model through feature engineering, regularization, batch normalization, and hyperparameter tuning, the optimized model (Model 2B) reached an accuracy of **76.42%** with a loss of **0.5131**. This represents a significant improvement in the model’s predictive ability and generalization.

The inclusion of new features such as `OVER_5000`, `FOR_PROFIT`, and `NAME_CATEGORY` enhanced the model’s ability to distinguish between successful and unsuccessful applicants. Additionally, the application of regularization and batch normalization helped stabilize training and prevent overfitting.

---

## **Future Improvements and Alternative Models**

Although the optimized deep learning model performed well, it may still be beneficial to explore alternative models such as **Random Forest** or **XGBoost**. These models are particularly well-suited for datasets with a large number of categorical features, like the one used in this project. 

Random Forest and XGBoost models often provide better interpretability through feature importance metrics, making them valuable in understanding which factors most influence the success of applicants. Furthermore, these models tend to require less tuning and can sometimes outperform deep learning models on structured data.

In future iterations of this project, experimenting with these models could lead to further improvements in predictive performance and offer greater transparency in decision-making.
