# Customer Churn Prediction using Artificial Neural Network (ANN)

A Deep Learning project that predicts whether a bank customer is likely to churn using an Artificial Neural Network (ANN).

This project implements an end-to-end ANN-based binary classification workflow, including data exploration, preprocessing, model training, evaluation, early stopping, hyperparameter tuning using GridSearchCV, and model artifact storage.

## 📌 Project Overview

Customer churn is an important business problem for banks and financial institutions. Identifying customers who are likely to leave allows organizations to take proactive customer-retention measures.

This project uses the Churn Modelling dataset to build an Artificial Neural Network that learns customer behavior patterns and predicts whether a customer will exit the bank.

### Objective

Predict whether a customer will churn:

- `0` → Customer will stay
- `1` → Customer will churn

The project also performs hyperparameter tuning using `GridSearchCV` to identify the best ANN configuration.

## 🧠 Project Workflow

    Raw Customer Dataset
            │
            ▼
    Data Loading
            │
            ▼
    Data Understanding & EDA
            │
            ▼
    Data Cleaning
            │
            ▼
    Feature Selection
            │
            ▼
    Train-Test Split
            │
            ▼
    Data Preprocessing
       ┌────┴────────────┐
       │                 │
       ▼                 ▼
    Numerical         Categorical
    Features          Features
       │                 │
       ▼                 ▼
    StandardScaler   OneHotEncoder
       └────┬────────────┘
            │
            ▼
    Preprocessed Features
            │
            ▼
    Artificial Neural Network
            │
            ▼
    Model Training
            │
            ▼
    Early Stopping
            │
            ▼
    Model Evaluation
            │
            ├── Accuracy
            ├── Precision
            ├── Recall
            ├── F1 Score
            └── ROC-AUC
            │
            ▼
    Hyperparameter Tuning
            │
            ▼
    GridSearchCV
            │
            ▼
    Best ANN Configuration
            │
            ▼
    Save Model & Preprocessor

## 📂 Dataset

The project uses the **Churn Modelling Dataset**.

### Dataset Size

- Rows: 10,000
- Columns: 14

### Features

| Feature | Description |
|---|---|
| RowNumber | Row identifier |
| CustomerId | Unique customer identifier |
| Surname | Customer surname |
| CreditScore | Customer credit score |
| Geography | Customer country |
| Gender | Customer gender |
| Age | Customer age |
| Tenure | Number of years with the bank |
| Balance | Account balance |
| NumOfProducts | Number of bank products used |
| HasCrCard | Whether the customer has a credit card |
| IsActiveMember | Whether the customer is an active member |
| EstimatedSalary | Estimated customer salary |
| Exited | Target variable |

### Target Variable

`Exited`

- `0` = Customer stayed
- `1` = Customer exited

## 🔍 Exploratory Data Analysis

The project performs data exploration and validation before model training.

The following checks are performed:

- Dataset shape
- Dataset information
- Descriptive statistics
- First few records
- Missing values
- Duplicate records
- Target distribution
- Numerical feature analysis
- Categorical feature analysis
- Feature selection

## ⚙️ Data Preprocessing

The dataset contains both numerical and categorical features.

### Numerical Features

Numerical features are standardized using:

`StandardScaler`

### Categorical Features

Categorical features are transformed using:

`OneHotEncoder`

Both transformations are combined using:

`ColumnTransformer`

The fitted preprocessing pipeline is saved as an artifact so that the same transformations can be reused later.

## 🤖 Artificial Neural Network

The project uses a feed-forward Artificial Neural Network built using **TensorFlow/Keras**.

### ANN Architecture

    Input Layer
         │
         ▼
    Dense Layer - 64 neurons
         │
         ▼
    Dense Layer - 64 neurons
         │
         ▼
    Output Layer - 1 neuron
         │
         ▼
    Sigmoid Activation

### Activation Functions

Hidden layers:

`ReLU`

Output layer:

`Sigmoid`

Since this is a binary classification problem, the sigmoid output represents the probability of customer churn.

## 🏋️ Model Training

The model is trained using:

- Optimizer: Adam
- Loss Function: Binary Crossentropy
- Metric: Accuracy
- Batch Size: 32
- Maximum Epochs: 100
- Validation Split: 20%

### Early Stopping

Early stopping is used to prevent unnecessary training and reduce overfitting.

The model monitors validation loss and restores the best model weights.

## 📊 Model Evaluation

The trained ANN is evaluated using multiple classification metrics.

### Metrics Used

**Accuracy**

Measures the overall percentage of correctly classified customers.

**Precision**

Measures how many customers predicted as churners actually churned.

**Recall**

Measures how many actual churners were correctly identified.

**F1 Score**

Provides a balance between precision and recall.

**ROC-AUC**

Measures the model's ability to distinguish between customers who churn and customers who stay.

## 📈 Model Results

The final baseline ANN achieved the following results on the test dataset:

| Metric | Score |
|---|---:|
| Accuracy | **86.30%** |
| Precision | **72.70%** |
| Recall | **52.33%** |
| F1 Score | **60.86%** |
| ROC-AUC | **86.00%** |

### Result Summary

- Accuracy: **86.30%**
- ROC-AUC: **86.00%**

The model demonstrates good classification performance on the customer churn dataset.

## 🔧 Hyperparameter Tuning

The project uses `GridSearchCV` to search for a better ANN configuration.

The following hyperparameters are explored:

- `neurons`
- `layers`
- `learning_rate`
- `batch_size`
- `epochs`

The search evaluates:

- 8 candidate configurations
- 3-fold cross-validation
- 24 total model fits

### Best Hyperparameters

The final GridSearchCV run selected:

| Hyperparameter | Best Value |
|---|---:|
| Batch Size | 32 |
| Epochs | 50 |
| Layers | 1 |
| Learning Rate | 0.001 |
| Neurons | 64 |

## 💾 Model Artifacts

The project saves the trained models and preprocessing pipeline inside the `artifacts` directory.

    artifacts/
    │
    ├── ann_model.h5
    ├── tuned_ann_model.h5
    └── preprocessor.pkl

### `ann_model.h5`

Contains the trained baseline ANN model.

### `tuned_ann_model.h5`

Contains the ANN model generated using the best hyperparameters found during GridSearchCV.

### `preprocessor.pkl`

Contains the fitted preprocessing pipeline, including numerical scaling and categorical encoding.

## 📁 Project Structure

    Customer_Churn_ANN_Project/
    │
    ├── artifacts/
    │   ├── ann_model.h5
    │   ├── tuned_ann_model.h5
    │   └── preprocessor.pkl
    │
    ├── data/
    │   └── Churn_Modelling.csv
    │
    ├── log/
    │
    ├── notebooks/
    │   └── ann.py
    │
    ├── .gitignore
    ├── main.py
    ├── pyproject.toml
    ├── README.md
    ├── requirements.txt
    └── uv.lock

## 🛠️ Technologies Used

### Programming Language

- Python

### Deep Learning

- TensorFlow
- Keras

### Machine Learning

- Scikit-learn
- SciKeras

### Data Processing

- Pandas
- NumPy

### Development Tools

- Visual Studio Code
- Git
- GitHub
- UV

## 📦 Installation

### 1. Clone the Repository

Replace `YOUR_USERNAME` with your GitHub username.

    git clone https://github.com/YOUR_USERNAME/Customer_Churn_ANN_Project.git

Move into the project directory:

    cd Customer_Churn_ANN_Project

### 2. Create a Virtual Environment

    python -m venv .venv

### Windows

    .venv\Scripts\activate

### Linux / macOS

    source .venv/bin/activate

### 3. Install Dependencies

    pip install -r requirements.txt

## ▶️ Running the Project

The main ANN implementation is located at:

    notebooks/ann.py

Run the project using:

    python notebooks/ann.py

If you are using UV:

    uv run python notebooks/ann.py

The script performs the following steps:

1. Loads the dataset
2. Performs data exploration
3. Checks data quality
4. Selects relevant features
5. Splits the dataset
6. Preprocesses numerical and categorical features
7. Builds the ANN
8. Trains the model
9. Applies early stopping
10. Evaluates the model
11. Saves the trained model
12. Performs GridSearchCV
13. Finds the best hyperparameters
14. Saves the tuned model

## 🧪 Example Output

    Evaluation Metrics:

    Accuracy: 0.8630
    Precision: 0.7270
    Recall: 0.5233
    F1 Score: 0.6086
    ROC AUC: 0.8600

Hyperparameter tuning:

    Starting hyperparameter tuning using GridSearchCV...

    Fitting 3 folds for each of 8 candidates,
    totalling 24 fits

    Best Hyperparameters found:

    {
        'batch_size': 32,
        'epochs': 50,
        'layers': 1,
        'learning_rate': 0.001,
        'neurons': 64
    }

## 🎯 Key Learning Outcomes

Through this project, the following concepts were implemented and practiced:

- Understanding binary classification
- Exploratory Data Analysis
- Data cleaning
- Feature selection
- Numerical feature scaling
- Categorical feature encoding
- Train-test splitting
- Artificial Neural Networks
- Dense layers
- ReLU activation
- Sigmoid activation
- Binary crossentropy
- Adam optimizer
- Model training
- Validation data
- Early stopping
- Classification metrics
- ROC-AUC
- Hyperparameter tuning
- GridSearchCV
- Cross-validation
- Model serialization
- Preprocessing pipeline serialization

## 🚀 Future Improvements

Possible improvements for future versions include:

- Building a Streamlit prediction interface
- Creating a REST API using FastAPI
- Adding confusion matrix visualization
- Adding ROC and Precision-Recall curves
- Experimenting with class-weight balancing
- Comparing ANN with traditional machine learning models
- Deploying the model to AWS
- Containerizing the application using Docker
- Implementing CI/CD using GitHub Actions

## 👨‍💻 Author

**Ajinkya Dhote**

B.Tech - Artificial Intelligence & Machine Learning

## ⭐ Project Highlights

- Built an Artificial Neural Network for customer churn prediction
- Implemented preprocessing using `ColumnTransformer`
- Used `StandardScaler` for numerical features
- Used `OneHotEncoder` for categorical features
- Implemented EarlyStopping
- Evaluated the model using multiple classification metrics
- Performed GridSearchCV-based hyperparameter tuning
- Evaluated 10,000 customer records
- Achieved **86.30% test accuracy**
- Achieved **0.86 ROC-AUC**
- Saved trained ANN models and preprocessing artifacts for reuse

## 📌 Note

This project was developed as part of Deep Learning learning and practice, with a focus on understanding the complete Artificial Neural Network workflow for binary classification.
