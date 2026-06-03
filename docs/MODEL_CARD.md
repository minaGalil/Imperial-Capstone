# Model Card: Hybrid BBO Optimisation Approach

## 1. Overview

**Model name:** Hybrid BBO Optimisation Framework
**Model type:** Surrogate-assisted black-box optimisation approach
**Version:** v1.0
**Task:** Sequential maximisation of eight unknown black-box functions
**Project:** Imperial BBO Capstone Project

This model card documents the optimisation strategy used to select query points for the BBO capstone challenge. The approach combines heuristic search, Gaussian Processes, SVM classification, neural-network surrogate modelling, CNN-inspired modelling, gradient-guided candidate generation and interpretability logs.

## 2. Intended Use

This approach is intended for educational and experimental black-box optimisation tasks where function evaluations are limited and the function structure is unknown. It is suitable for exploring how different ML techniques can guide sequential decision-making under uncertainty.

Appropriate uses include:

* capstone query generation
* surrogate-assisted optimisation experiments
* exploration-exploitation analysis
* small-scale optimisation research
* documentation of iterative ML decision-making

This approach should not be used as a production optimiser without additional validation, benchmarking and robustness testing. It is also not intended for high-stakes decisions where errors could affect safety, finance, healthcare or people’s rights.

## 3. Model Details and Strategy Evolution

The strategy evolved across multiple rounds.

In the early rounds, the approach used heuristic local search by selecting points near the current best observed input. This was simple and interpretable but limited because it did not use the full dataset.

Later, Gaussian Process modelling was introduced to estimate both predicted output and uncertainty. This supported Bayesian-style optimisation using acquisition logic such as UCB.

SVM classification was then added to separate high-performing and low-performing regions. This helped guide the search toward promising areas while adding interpretability through decision-boundary thinking.

Neural-network surrogate models were introduced to capture more complex non-linear relationships, especially in higher-dimensional functions. Gradient-based search was added to move candidate points in directions predicted to improve output.

CNN-inspired surrogate modelling was later introduced to reflect concepts from deep learning, including feature hierarchy, gradient sensitivity and feature importance. The approach also added adaptive exploration, temperature-style control, attention-style weighting, diversity bonuses and decision logs to improve transparency.

By Week 10, the system used a hybrid scoring framework combining:

* GP uncertainty and UCB
* SVM promising-region probability
* MLP prediction
* CNN-inspired prediction
* gradient strength
* attention-style recency weighting
* diversity bonus
* interpretability logs

## 4. Inputs and Outputs

**Inputs:**
Each function receives a vector of numerical values between 0 and 1.

Example for a 2D function:

`0.123456-0.654321`

**Outputs:**
The capstone portal returns one numerical value for each submitted query. Since the problem is a maximisation task, higher values indicate better performance.

The model itself outputs:

* recommended query point
* portal-formatted query string
* predicted/supporting model scores
* feature importance estimates
* decision reasoning logs

## 5. Performance Summary

Performance is evaluated by tracking improvement in observed output values across rounds for each of the eight functions. The main performance indicators are:

* current best output per function
* improvement over previous best
* stability of performance across rounds
* exploration-exploitation balance
* whether new queries discover better regions
* interpretability of the selected query

The strongest improvements were observed in functions where promising regions became clearer over time. Some functions showed diminishing returns, suggesting either local convergence or insufficient exploration of alternative regions.

## 6. Assumptions and Limitations

The approach assumes that historical input-output observations contain useful structure for guiding future queries. It also assumes that nearby points may have related output behaviour and that surrogate models can approximate useful patterns from a small dataset.

Key limitations include:

* small number of observations
* risk of overfitting surrogate models
* limited coverage of high-dimensional spaces
* possible sampling bias toward previously strong regions
* no guarantee of finding the global optimum
* computational cost from using multiple models
* difficulty validating model predictions without additional portal evaluations

The approach may fail when the underlying function is highly discontinuous, extremely noisy or contains strong optima far from previously sampled regions.

## 7. Ethical Considerations

This project does not use personal or sensitive data. However, transparency and documentation remain important because the optimisation process involves modelling assumptions, uncertainty and decision-making under limited information.

The model card supports responsible ML practice by explaining what the optimisation approach does, what assumptions it makes, where it may fail and how decisions are made. This improves reproducibility and helps other researchers, facilitators or employers understand and evaluate the work.

## 8. Reproducibility and Documentation

To support reproducibility, the repository should include:

* weekly notebooks
* historical input/output files
* submission logs
* feature-importance files
* decision logs
* README documentation
* datasheet
* model card

The decision log is especially important because it records not only the final query but also the reasoning and model components that influenced the choice.

## 9. Future Improvements

Future improvements may include:

* stronger Bayesian optimisation using BoTorch
* automated hyperparameter tuning with Optuna
* Expected Improvement or Probability of Improvement acquisition functions
* ensemble surrogate comparison
* better validation of model uncertainty
* visual dashboards for optimisation progress
* clearer benchmarking across functions and rounds

## 10. Final Note

This BBO optimisation approach is best understood as an evolving research framework rather than a finished production optimiser. Its main value is in demonstrating thoughtful iteration, transparent reasoning, responsible documentation and practical ML decision-making under uncertainty.

