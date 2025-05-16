# Charity Funding Prediction Report  

## Overview of the Analysis  
The purpose of this analysis was to develop a deep learning model capable of predicting whether applicants to the Alphabet Soup charity organization would be successful in their business ventures. This allows the organization to optimize their decision-making process and focus resources on promising applicants.

---

## Results  

### **Data Preprocessing**

- **Target Variable:**
  - `IS_SUCCESSFUL` (Binary: 1 if venture was successful, 0 otherwise)

- **Feature Variables:**
  - All remaining columns after dropping `EIN` and `NAME` were used, including categorical variables transformed using one-hot encoding. These features represented applicant demographics, financials, and application details.

- **Removed Variables:**
  - `EIN` and `NAME` were removed as they do not contribute to the predictive capabilities of the model.

---

### **Compiling, Training, and Evaluating the Model**

- **Initial Neural Network Model: 'Starter_Code.ipynb'**
  - **Layers:** 2 hidden layers  
  - **Neurons:** 80 in the first layer, 30 in the second layer  
  - **Activation Functions:** `relu` for hidden layers, `sigmoid` for output  
  - **Performance:** Achieved ~73% accuracy  
  - **Reasoning:** This baseline configuration used a common activation function (`relu`) for handling non-linear relationships and a `sigmoid` activation in the output layer for binary classification.

- **Model Optimization Attempts:'AlphabetSoupCharity_Optimization.ipynb'**
  - Utilized **Keras Tuner** with **Hyperband** optimization across three versions of models:
    1. Tuned neuron counts and activation functions (`relu`, `tanh`, `sigmoid`).
    2. Increased layer sizes and added options like `selu` and `leaky_relu`.
    3. Included **regularization**, **dropout layers** (0.2, 0.3, 0.5), and **learning rate tuning** (0.001, 0.005, 0.01).

  - **Best Model Configuration Found:**
    - Activation Function: `sigmoid`
    - Layers: 3 hidden layers with dropout regularization
    - Neurons: Ranged from 16 to 128 per layer
    - Learning Rate: Tuned using Adam optimizer
    - **Final Accuracy:** Approximately 73.5% on validation data  

- **Steps Taken to Improve Model Performance:**
  - **Hyperparameter Tuning:** Used Keras Tuner to explore optimal combinations of neurons, layers, activation functions, and learning rates.
  - **Regularization:** Added dropout layers and L2 regularization to reduce overfitting.
  - **Activation Function Exploration:** Tested `relu`, `tanh`, `selu`, `leaky_relu`, and `sigmoid` activation functions to optimize non-linear learning.
  - **Early Stopping:** Implemented early stopping to prevent overfitting and reduce unnecessary training time.
  - **Learning Rate Tuning:** Adjusted learning rates using the Adam optimizer for better convergence.

---

## Summary  

Although significant tuning was performed, the best deep learning model achieved a validation accuracy of approximately **73.5%**, falling short of the target accuracy goal of **75%**. This suggests that a neural network may not be the optimal solution for this classification problem with the available data.

It is recommended to explore alternative machine learning models such as:

- **Random Forest Classifier:** Handles categorical variables well and provides insight into feature importance.
- **XGBoost Classifier:** Known for strong performance on structured data and effective handling of class imbalances.

Using these ensemble models could potentially achieve higher accuracy and offer more interpretable results for the organization’s decision-making process.


