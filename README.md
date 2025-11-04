# Impact-of-Rock-Climbing-on-Bird-Populations
*An Ecological Data Science Case Study*

---

## Overview 

This project investigates how outdoor climbing activity may influence bird diversity and conservation value in cliff environments. Using ecological survey data from **32 climbing cliffs in Boulder, Colorado**, the analysis models the **Community Conservation Value (CCV)**: a composite metric of avian species richness, relative abundance, and conservation importance.

While the dataset comes from a previously published ecological study, this project independently reproduces and extends the analysis using **statistical and machine learning methods implemented in R**, including linear regression, regularized regression (lasso and ridge), and random forest modeling.

The primary goal was to explore relationships between climbing activity, cliff characteristics, and bird diversity using modern data-science techniques, while comparing model interpretability and performance.

---


## Data Source & Reference

The dataset analyzed here originates from the published ecological study:

> Covy, N., Benedict, L., & Keeley, W. H. (2019).  
> *Rock climbing activity and physical habitat attributes impact avian community diversity in cliff environments.*  
> *PLOS ONE*, 14(1): e0209557.  
> [https://doi.org/10.1371/journal.pone.0209557](https://doi.org/10.1371/journal.pone.0209557)

The raw data are publicly available and linked above.

This analysis **reproduces and extends** the study’s findings using simplified and independently written R code.  
Whereas the original paper applied detailed ecological modeling, this project focuses on:

- Rebuilding the analysis pipeline in RMarkdown,  
- Applying **regularized regression (ridge and lasso)** and **random forest** models for comparison, and  
- Evaluating predictor significance, multicollinearity, and model performance using standard data-science methods.

---

## Methods

### Exploratory Data Analysis
- Cleaned and standardized column names.  
- Examined numeric and categorical predictor distributions via boxplots.  
- Checked for multicollinearity using **Variance Inflation Factors (VIF)** and **correlation matrices** (`corrplot`).

### Modeling
- **Linear Regression** – baseline model for interpretability.  
- **Backward Stepwise Selection** – feature selection using Bayesian Information Criterion (BIC).  
- **Lasso & Ridge Regression** – penalized models to address correlated predictors (`glmnet`).  
- **Random Forest** – nonlinear benchmark with variable importance (`randomForest`).

### Model Evaluation
- Train/test split (70/30).  
- Comparison based on test **Mean Squared Error (MSE)** and qualitative variable-importance rankings.  
- Interpretation focused on ecological meaning of significant predictors.

---

## Results

All modeling approaches consistently showed that **environmental and physical cliff characteristics** were the primary predictors of avian Community Conservation Value (CCV), while **human climbing activity had minimal effect**.

- **Linear and stepwise regression** identified *Aspect* (cliff direction) and, to a lesser extent, *Climbers_Present* and *Total_Climbing_Routes* as weakly significant predictors, but overall model fit was low.  
- **Regularized models** reinforced these results:  
  - *Ridge regression* (MSE ≈ **24.7**) retained small coefficients for *Temperature*, *Height*, and *Vertical_Angle*.  
  - *Lasso* (MSE ≈ **26.2**) shrank climbing-related predictors (*Climbing_Use*, *Climbers_Present*) to zero, indicating negligible impact.  
- **Random forest** achieved the best performance (MSE ≈ **20.8**) and ranked *Temperature*, *Height*, and *Vertical_Angle* as the most important features.  

Overall, **natural cliff attributes dominated CCV prediction**, while climbing variables showed only minor or statistically insignificant effects, complementing the findings of the original study but derived here through regression and machine-learning methods.

---

## Limitations

- **Small sample size** (n = 32) limits model robustness.  
- **No control group** of non-climbing cliffs was surveyed, restricting causal inference.  
- **Collinearity** between many geographic variables (elevation, height, aspect) complicates direct interpretation.  
- **Confounding ecological factors** (e.g., nesting preferences, microclimate) likely contribute to CCV variance beyond the measured predictors.














