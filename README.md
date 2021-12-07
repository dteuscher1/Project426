# Importance of Hustle Stats in the NBA

## Introduction

NBA analysts frequently mention "hustle" as a key to winning the game. If a team "hustles" more, then they are more likely to win. In this project, we were interested in the impact that hustle stats actually have in a team winning or losing an NBA game and whether the numbers will back up the claims that analysts ofetn make.

## Data Collection & Cleaning

The data used for the project was collected using the [`nba-api`](https://pypi.org/project/nba-api/) python package which is an API Client for (https://www.nba.com). Team-specific hustle data was collected for the 2018-2019 and 2020-2021 seasons. The 2019-2020 season was left out due to it being the COVID-19 shortened season that was resumed in the bubble and is very much an anomaly in recent history. For this project, we designated hustle stats as the following:
- Deflections
- Contested shots (broken down by 2s and 3s)
- Charges
- Screen assists
- Loose balls recovered 
- Boxouts (Offensive and Defensive)

In terms of formatting the data, the ratio and difference were calculated for each of the designated hustle stats. Additionally, the ratios and differences of hustle stats were further subset into home and away. This gave us four datasets to model with: 
- `home_difference`
- `home_ratio`
- `away_Difference`
- `away_ratio`

## Exploratory Data Analysis (EDA)

## Methods

Initially, five different types of models were fit to each of the four datasets:
- Logistic Regression
- K Nearest Neighbors
- Random Forest
- Gradient Boosted Machine
- Extreme Gradient Boosted Machine

Below are the out-of-sample accuracies for each of the models:

| Data | Logistic | KNN | Random Forest | GBM | XGBoost |
| ----------- | ----------- |----------- |----------- |----------- |----------- |
| `away_difference` | 0.617 | 0.605 | 0.614 | 0.597 | 0.601 |
| `home_difference` | 0.628 | 0.599 | 0.607 | 0.596 | 0.609 |
| `away_ratio` | 0.616 | 0.602 | 0.597 | 0.591 | 0.614 |
| `home_ratio` | 0.626 | 0.579 | 0.590 | 0.578 | 0.603 

Additionally, we looked at the four ROC curves for each of the models:

### Logistic

![Logistic ROC](https://github.com/dteuscher1/Project426/blob/main/PNGs/Logistic%20ROC.png)

### KNN

![KNN ROC](https://github.com/dteuscher1/Project426/blob/main/PNGs/KNN%20ROC.png)

### Random Forest

![Random Forest ROC](https://github.com/dteuscher1/Project426/blob/main/PNGs/Random%20Forest%20ROC.png)

### GBM

![GBM ROC](https://github.com/dteuscher1/Project426/blob/main/PNGs/GBM%20ROC.png)

### XGBoost

![XGBoost ROC](https://github.com/dteuscher1/Project426/blob/main/PNGs/XGBoost%20ROC.png)

## Results

Overall, the best model for this analysis was a Logsitic Regression model with the `home_difference`data set. 

## Conclusion

