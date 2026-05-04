###Suzuki Stock Market Prediction
This project explores various machine learning approaches to predict the stock performance of Suzuki. The repository documents a transition from traditional regression-based forecasting to a more robust classification strategy using advanced feature engineering.

📉 ##Project Evolution & Methodology
1. The Regression Phase (Random Forest & XGBoost)
Initially, I implemented Random Forest and XGBoost Regressors using historical data sourced from Kaggle.

The Problem: While these models showed high accuracy on the test set, they suffered from significant overfitting.

The Outcome: The models failed to generalize to new, unseen data and struggled with extrapolation (predicting values outside the range of the training set), making them unreliable for live market scenarios.

2. The Time Series Phase (SARIMAX)
To account for seasonality, I shifted to SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous regressors).

The Problem: Upon analyzing the result plots, it became clear that SARIMAX tended to follow a linear trend (either strictly upward or downward).

The Outcome: It failed to capture the volatile fluctuations and "zig-zag" nature of real-world stock movements.

3. The Pivot: Classification Strategy
Realizing that predicting the exact price is a "noisy" task, I reframed the problem: Will the price go Up or Down?

The Solution: I implemented a Random Forest Classifier.

The Result: By shifting from regression to binary classification, the model achieved much higher reliability and better performance metrics.

🛠️ ##Feature Engineering
A key breakthrough in this project was moving away from raw "High, Low, Close" prices, which often lead to data leakage or lagging predictions. Instead, I focused on Stationary Features and Momentum Indicators:

Returns: Calculated percentage change in closing prices to normalize the data.

Lag Features: Created lag1 and lag2 features to provide the model with historical context from previous time steps.

Rolling Statistics: Implemented a rolling_mean and rolling_std (window of 3) to capture local trends and volatility fluctuations.

Why this works: These features transform the data from absolute values to relative movements, allowing the model to recognize patterns regardless of the specific price level.

🚀 ##Key Insights
Extrapolation Limits: Tree-based regressors cannot predict values higher or lower than what they have seen in the training set.

Classification > Regression: In high-volatility environments, predicting direction (trend) is often more effective than predicting absolute value.

Feature Selection: Engineering lags and rolling windows is more effective for time-series than using raw price data.

💻 ##Tech Stack
Language: Python

Libraries: Pandas, NumPy, Scikit-learn, XGBoost, Statsmodels, Matplotlib/Seaborn

Dataset: Suzuki Historical Stock Data (Kaggle)
