# Hospital Sales Prediction Using SuperLearner and Deep Learning

This repository contains a project focused on maximizing sales of orthopedic products to hospitals in the United States. By identifying non-customer hospitals that are similar to existing customers, the project aims to optimize sales efforts and expand the customer base. The approach combines propensity score estimation using the SuperLearner algorithm with deep learning for sales prediction.

## Project Overview

The project addresses a critical business challenge: identifying hospitals with high potential for sales growth. Using a dataset of over 4,000 hospitals, the analysis:
- Estimates propensity scores to identify non-customer hospitals likely to become customers.
- Uses deep learning to predict potential sales for these hospitals.
- Provides actionable insights for targeted sales campaigns.

## Data

The project uses the "hospitalUSA" dataset, which includes the following variables:
- ZIP code
- Hospital ID
- City
- State
- Number of beds (total and rehab)
- Outpatient visits
- Administrative costs
- Inpatient revenue
- Sales of rehab equipment
- Number of hip/knee/femur operations
- Indicators for teaching hospitals, trauma units, and rehab units

## Methods

1. **Data Preparation**:
   - A binary target variable (`C`) was created: `C=1` for current customers (SALES > 0) and `C=0` for non-customers (SALES = 0).
   - Data was transformed using a custom `transgap` function to minimize skewness and gaps.

2. **Propensity Score Estimation**:
   - The SuperLearner algorithm was used to ensemble multiple models (e.g., GLM, Random Forest, SVM, Neural Networks, MARS) for binary classification.
   - Propensity scores were calculated, and hospitals with scores between 0.35 and 0.65 were targeted as potential customers.

3. **Deep Learning Model**:
   - A deep learning model was trained on customer data to predict sales.
   - Predictions were made for non-customer hospitals with intermediate propensity scores.

4. **Variable Selection**:
   - Factor analysis and Random Forest variable importance were used to identify key drivers of sales.

## Results

- The top 10 non-customer hospitals with the highest predicted sales potential were identified.
- These hospitals are primarily located in the Northeast and Northwest, aligning with the geographic distribution of high-sales current customers.
- Potential sales were quantified by city and state, with predictions reported in thousands of dollars.

## How to Use

1. **Install Required Packages**:
   ```R
   install.packages(c("SuperLearner", "caret", "randomForest", "h2o", "dplyr", "ggplot2", "psych"))


## Future Enhancements

- Further optimize hyperparameters for the SuperLearner and deep learning models.
- Explore additional feature engineering techniques.
- Apply interpretability techniques to the deep learning model for better understanding of predictions.

## Citations

- Dataset: "hospitalUSA"
- R packages: SuperLearner, caret, randomForest, h2o, dplyr, ggplot2, psych.
