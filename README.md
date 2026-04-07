# Imperial-Capstone

## 🔹Section(1): Project Overview

Black-Box Optimisation (BBO) Capstone Project

This project focuses on solving a Black-Box Optimisation (BBO) challenge, where the goal is to maximise a set of unknown functions using limited observations. The internal structure of these functions is hidden, meaning decisions must be made based only on input-output interactions.

The core objective is to iteratively propose optimal input values (queries) that lead to the highest possible output. Each iteration provides new feedback, allowing the strategy to evolve over time.

Why is this relevant in real-world ML?

This challenge closely mirrors real-world scenarios where:

the underlying system is unknown or too complex to model directly
evaluations are expensive or limited (e.g. A/B testing, hyperparameter tuning, drug discovery)
decisions must be made under uncertainty
Instead of relying on full knowledge, we rely on data-driven exploration and intelligent search strategies.

Career Relevance

This project strengthens key data science skills such as:

optimisation under uncertainty
iterative model improvement
balancing exploration vs exploitation
applying ML techniques in real-world constraints
These are directly applicable to roles involving:

ML engineering
data science
decision intelligence systems
optimisation problems in business environments

## 🔹Section(2): Inputs and Outputs

Inputs

Each function receives a vector of input values:   x1-x2-x3-...-xn

Where:

each value is between 0 and 1
each value is formatted to 6 decimal places
the number of dimensions varies per function (2D → 8D)
Example: 0.123456-0.654321

Outputs

For each submitted input, the system returns:

a single numerical output value
representing the performance of that input
This output is used to:

update the dataset
guide the next optimisation step

## 🔹Section(3): Challenge Objectives

The objective of this project is to:

Maximise the output of each black-box function

Key Constraints

Limited number of queries per function
No knowledge of the underlying function
Sequential feedback (one new data point per round)
Increasing dimensionality (from 2D to 8D)
Challenges

Identifying promising regions with limited data
Avoiding local optima
Managing uncertainty in high-dimensional spaces
Designing strategies that improve over time
 

## 🔹Section(4): Technical Approach

This project follows an iterative optimisation strategy, evolving across multiple rounds.

Week 1 – Heuristic Local Search

Strategy:
Identify best-performing input
Apply small perturbations around it
Approach:
Simple exploitation-based search
Minimal exploration
Limitation:
No global understanding of the function
Risk of getting stuck in local optimum
Week 2 – Bayesian Optimisation (Gaussian Process)

Introduced:
Gaussian Process (GP) as surrogate model
Upper Confidence Bound (UCB) acquisition function
Strategy:
Use predicted mean + uncertainty
Balance exploration and exploitation
Improvements:
Uses full dataset
Incorporates uncertainty
More structured decision-making
Week 3 – Hybrid Model (GP + SVM)

Added:
Support Vector Machine (SVM) classifier
Classifies regions into:
high-performance
low-performance
Strategy:
Combine:
GP prediction (mean + uncertainty)
SVM probability of promising regions
Final selection based on: Hybrid Score = UCB × SVM Probability
Benefit:

Better interpretability
Improved control over search regions
More efficient exploration in high dimensions
## 🔹Section(5): Exploration vs Exploitation Strategy

The approach dynamically balances:

Exploitation
Focus on high-performing regions
Local refinement around best points
Exploration
Sampling uncertain or untested regions
Prevents early convergence

## 🔹Optimisation Workflow

```mermaid
flowchart TD
    A[Initial Dataset] --> B[Train Gaussian Process Model]
    B --> C[Generate Candidate Points]
    C --> D[Compute GP Predictions (Mean + Uncertainty)]
    D --> E[Apply UCB Acquisition Function]

    B --> F[Train SVM Classifier (High vs Low Regions)]
    F --> G[Predict Probability of Promising Region]

    E --> H[Combine Scores]
    G --> H

    H --> I[Select Best Candidate]
    I --> J[Submit Query]
    J --> K[Receive Output]
    K --> A



👉 This shows:
- full pipeline
- iterative loop
- GP + SVM integration

🔥 This alone impresses reviewers.

---

# 🔷 2. GP vs SVM Concept Diagram

Add this section:

```markdown
## 🔹 Model Architecture: GP vs SVM

```mermaid
flowchart LR
    A[Input Data (X, y)] --> B[Gaussian Process]
    A --> C[SVM Classifier]

    B --> D[Predict Mean & Uncertainty]
    C --> E[Classify Regions (High vs Low)]

    D --> F[UCB Score]
    E --> G[Region Probability]

    F --> H[Hybrid Decision]
    G --> H

    H --> I[Next Query Point]


---

# 🧠 Explain it below the diagram

Add this text:

```markdown
The Gaussian Process models the expected output and uncertainty, enabling exploration through the acquisition function.  
The SVM classifier identifies promising regions by separating high-performing and low-performing areas.  
Both models are combined into a hybrid decision strategy to guide the next query.

dimensionality
model uncertainty
observed performance trends
