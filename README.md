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

In terms of formatting the data, the ratio and difference were calculated for each of the designated hustle stats. Additionally, the ratios and differences of hustle stats were further subset into home and away. We did this so that there would not be repeat information in each row. We wanted our models to look at just the home team or just the away team's hustle stats. This gave us four datasets to model with: 
- `home_difference`
- `home_ratio`
- `away_Difference`
- `away_ratio`

## Exploratory Data Analysis (EDA)

![SCRREN_AST_RATIO Hist](https://github.com/dteuscher1/Project426/blob/main/PNGs/SCREEN_AST_RATIO%20Hist.png)

![DEFLECTION_RATIO Hist](https://github.com/dteuscher1/Project426/blob/main/PNGs/DEFLECTION_RATIO%20Hist.png)

![DEFLECTIONS_DIFF Hist](https://github.com/dteuscher1/Project426/blob/main/PNGs/DEFLECTIONS_DIFF%20Hist.png)

![DEF_BOXOUT_DIFF Hist](https://github.com/dteuscher1/Project426/blob/main/PNGs/DEF_BOXOUT_DIFF%20Hist.png)

![OFF_BOXOUT_DIFF Hist](https://github.com/dteuscher1/Project426/blob/main/PNGs/OFF_BOXOUT_DIFF%20Hist.png)

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

Looking at the out-of-sample accuracy metrics and ROC curves foe each model, we determined that the best model for this analysis was a Logsitic Regression model with the `home_difference`data set. Although, it is interesting to note that the team that was favored to win won apporximately 67% of the time and that our Logistic Regression model had an accuracy below this. Additionally, during the process of model fitting, we noticed that all the machine learning-based algorithms overfit to the training data sets and had in-sample accuracies arond 70-80% while the out-of-sample accuracies were around 60%. Also, we founc that overall, the difference in hustle stats was slightly more informative that the ratio in hustle stats.

## Conclusion

Overall, it seems that hustle plays on their own do not have a significant impact on winning or losing an NBA game as simply choosing the favored team results in a better accuracy than merely looking at hustle stats. Although, we believe there are other analysis that could be performed to further study this hypothesis:
- We could look at NBA games where there is not a clear favorite to win and see if hustle stats do better a predicting "close" games
- We could look at win probability or expected points added as the response variable instead of simply a binary win/loss variable
- Hustle stats could be combined with regular box score data to see if any of the hustle stats come back as significant towards determining a win or a loss.
- Include additional data and see if the addition of hustle plays improves model accuracy
- Obtain spatial and temporal data to better quantify hustle for players (how much they are moving, how quickly, etc...)
