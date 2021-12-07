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

## Methods and Results

Initially, five different types of models were fit to each of the four datasets:
- Logistic Regression
- K Nearest Neighbors
- Random Forest
- Gradient Boosted Machine
- Extreme Gradient Boosted Machine

Additionally, we looked at the four ROC curves for each of the models:



## Conclusion

