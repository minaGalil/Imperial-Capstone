
# Datasheet: BBO Capstone Query History Dataset

## 1. Motivation

This dataset was created for the Black-Box Optimisation (BBO) capstone project. The purpose of the dataset is to support iterative optimisation of eight unknown black-box functions using limited query opportunities. Each round adds new input-output observations, allowing the optimisation strategy to improve over time through evidence, modelling and reflection.

The dataset helps solve a sequential optimisation problem where the internal function equations are unknown. It supports experimentation with optimisation techniques such as heuristic search, Gaussian Process modelling, SVM classification, neural-network surrogate modelling, CNN-inspired modelling, gradient-based candidate generation and adaptive exploration-exploitation strategies.

## 2. Dataset Composition

The dataset contains query histories for eight synthetic black-box functions. Each function has a different input dimensionality, ranging from 2D to 8D. Each data point consists of an input vector and one numerical output value returned by the capstone portal.

Each input value is constrained between 0 and 1 and must be submitted in the format:

`0.xxxxxx-0.xxxxxx-...`

Each output represents the observed performance value for the submitted query. The task is a maximisation problem, so higher output values are considered better.

The dataset currently includes the initial observations provided by the capstone challenge and additional submitted query results from weekly iterations. The dataset is small by design because the challenge simulates expensive or limited evaluations.

## 3. Collection Process

The initial data points were provided as part of the capstone challenge. Additional data points were collected weekly by submitting one query per function through the capstone portal. After each submission, the returned output value was appended to the query history.

The collection process is sequential and iterative. Each new query is informed by previous observations, model predictions, uncertainty estimates and exploration-exploitation trade-offs.

No human-subject data, personal data or sensitive demographic data is included in this dataset.

## 4. Preprocessing and Cleaning

The main preprocessing steps include checking input dimensions, ensuring all input values remain within the valid range [0, 1], formatting query strings to six decimal places and appending new input-output pairs without duplicating existing records.

Additional processing includes scaling features for machine learning models, generating feature-importance estimates and maintaining submission logs for reproducibility.

Raw query inputs and outputs are preserved as historical records so that the optimisation process can be audited and reproduced.

## 5. Intended Uses

This dataset is intended for:

* studying black-box optimisation under limited evaluations
* testing surrogate models
* comparing exploration and exploitation strategies
* tracking optimisation progress across weekly rounds
* supporting capstone documentation and reflection

It should not be used as a general benchmark for real-world industrial optimisation because the functions are synthetic and the evaluation environment is specific to the capstone challenge.

## 6. Distribution

The dataset and related outputs are intended to be stored in the GitHub repository for educational and capstone documentation purposes. The repository structure should clearly separate notebooks, data, results, images and documentation.

Suggested location:

`data/` for raw or structured query history
`results/` for weekly submission outputs and logs
`docs/` for documentation files

## 7. Maintenance

The dataset should be updated after each weekly query round. Maintenance includes adding the latest submitted inputs, adding returned outputs, checking formatting consistency, preserving older versions and updating documentation when the strategy changes.

The repository owner is responsible for maintaining the dataset, keeping the README current and ensuring that datasheet details remain aligned with the latest capstone progress.

## 8. Known Limitations

The dataset is intentionally small, which limits model certainty and increases the risk of overfitting. Higher-dimensional functions are especially difficult because the number of observations covers only a small part of the search space. Some regions may be underexplored because earlier strategies focused more heavily on promising areas. Therefore, the dataset reflects both the true function responses and the sampling choices made during the capstone process.
