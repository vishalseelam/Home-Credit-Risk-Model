
# Home Credit Default Prediction

![Home Credit Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/Home_Credit_Group_logo.svg/1200px-Home_Credit_Group_logo.svg.png)

This repository contains the code and resources used to develop a machine learning model that predicts the likelihood of a customer defaulting on a loan. The project was part of the Home Credit Kaggle competition and focuses on creating a robust and stable model that performs well both in the present and future, minimizing the risk of performance degradation.

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Installation](#installation)
- [Data Processing](#data-processing)
- [Feature Engineering](#feature-engineering)
- [Model Training](#model-training)
- [Evaluation](#evaluation)
- [Submission](#submission)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The goal of this project is to predict loan defaults using customer data provided by Home Credit. A key aspect of this competition is the custom scoring metric, which penalizes models that decline in performance over time. The project utilizes advanced data processing techniques, feature engineering, and a LightGBM model to deliver reliable predictions.

## Data Sources

The data used in this project is sourced from the [Home Credit Default Risk](https://www.kaggle.com/c/home-credit-default-risk) Kaggle competition. You can access the datasets via the following path:

```
/kaggle/input/home-credit-credit-risk-model-stability/
```

### Data Files
- `train/train_base.csv`
- `train/train_static_0_0.csv`
- `train/train_static_0_1.csv`
- `train/train_static_cb_0.csv`
- `train/train_person_1.csv`
- `train/train_credit_bureau_b_2.csv`
- `test/test_base.csv`
- `test/test_static_0_0.csv`
- `test/test_static_0_1.csv`
- `test/test_static_0_2.csv`
- `test/test_static_cb_0.csv`
- `test/test_person_1.csv`
- `test/test_credit_bureau_b_2.csv`

## Installation

To set up the project on your local machine, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/home-credit-default-prediction.git
    cd home-credit-default-prediction
    ```

2. Create and activate a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Data Processing

The data processing pipeline leverages Polars for efficient data handling and manipulation. Key steps include:
- Loading and merging multiple datasets.
- Handling missing values and converting data types for optimal memory usage.
- Aggregating data to create features that enhance model performance.

## Feature Engineering

Feature engineering is critical to improving the model's predictive power. Key features include:
- Aggregation of income, occupation, and credit bureau data.
- Handling of categorical variables with custom category handling for unseen data.
- Selection of high-impact features for the final model.

## Model Training

A LightGBM model is trained with a focus on accuracy and stability. Key training parameters include:
- Boosting type: Gradient Boosting Decision Trees (GBDT)
- Objective: Binary Classification
- Metrics: AUC (Area Under the Curve)
- Hyperparameters: Learning rate, max depth, number of leaves, etc.

Early stopping and feature selection were employed to avoid overfitting and optimize model performance.

## Evaluation

The model's performance is evaluated using:
- **AUC Score**: Measures the model's ability to differentiate between classes.
- **Gini Stability Metric**: Custom metric that assesses the stability of the model's performance over time, penalizing declines.

## Submission

The final predictions are generated and prepared for submission. Special handling is implemented to manage unseen categories in the test data, ensuring robust predictions.

## Contributing

Contributions are welcome! Please follow these steps to contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
