# Stock Market Strategy Prediction

## Project Overview

This project aims to predict stock market strategies using advanced machine learning techniques. It involves preprocessing historical stock data, engineering relevant features, building an ensemble classifier, and evaluating its performance. The prediction of stock strategies involves forecasting the closing price using SARIMAX and MLR models, which are then used as inputs in the ensemble classifier for strategy prediction.

## Detailed Approach

### Data Loading and Preprocessing

1. **Data Loading**: Historical stock data was loaded from `train.csv`.
2. **Technical Indicators Calculation**:
   - Relative Strength Index (RSI) for Close and Open prices.
   - Rate of Change (ROC) for Close prices.
   - Moving Average Convergence Divergence (MACD) and MACD Histogram for Close prices.
   - Exponential Moving Average (EMA) for Close and Open prices.
   - Rolling Mean for Open prices.
   - Bollinger Bands Percentage (Volatility_BVP) for Close prices.
   - Open-Close Difference.
3. **Missing Values Handling**: SimpleImputer was used to handle missing values.
4. **Feature Selection**: The dataset was split into features (X) and the target variable (y) using the calculated indicators.

### Time Series Forecasting with SARIMAX and MLR

1. **SARIMAX**: Used for forecasting closing prices.
2. **Multiple Linear Regression (MLR)**: Applied to predict closing prices using features like opening price, volume, and technical indicators.

### Model for Strategy

1. **Relation Between Closing Price Prediction and Strategy**:
   - The forecasted closing prices are crucial inputs for strategy decisions. For example, an expected increase in closing price might suggest a 'buy' strategy, while a predicted decrease might suggest a 'sell' strategy.
   - By providing predicted future prices, the SARIMAX and MLR models help in making informed strategy predictions.
2. **Feature Engineering**: 
   - Features such as RSI, ROC, MACD, EMA, Rolling Mean, Volatility_BVP, and Open-Close Difference were calculated and used in the model.
3. **Model Building**:
   - Constructed an ensemble classifier (VotingClassifier) comprising:
     - Random Forest Classifier (RandomForestClassifier).
     - XGBoost Classifier (XGBClassifier).
   - Adjusted weights for models in the ensemble to optimize performance.
4. **Training and Evaluation**:
   - Split the dataset into training and testing sets.
   - Trained the ensemble classifier on the training data.
   - Evaluated model performance using accuracy metrics on the test set.
   - The accuracy of the ensemble classifier was calculated as 88.33%.
   - A classification report was generated to provide a detailed performance analysis.

### Prediction and Output

1. **Strategy Prediction**: The trained ensemble classifier was used to predict stock market strategies for a provided dataset.
2. **Output**: Predictions along with relevant data (id, Date, Close Price, Strategy) were saved to a CSV file (`submission.csv`).

### Correlation Analysis

1. **Correlation Calculation**: Correlation between the target variable 'Strategy' and the features was calculated to understand the relationships and the influence of each feature on the target variable.
2. **Results**: The correlation results helped in selecting the most relevant features for the model, ensuring that the model predictions are based on significant and impactful data points.

## Analysis and Verification

The integration of SARIMAX and MLR for predicting closing prices ensures that the ensemble classifier receives accurate inputs for determining stock market strategies based on predicted future prices. This structured approach provides robust predictions by combining time series forecasting with machine learning classification techniques.

## Conclusion

The project methodology leverages time series forecasting (SARIMAX and MLR) and machine learning classification (ensemble classifier) to predict stock market strategies effectively. By integrating these techniques, the model achieves accurate strategy predictions based on historical data and technical indicators. The accuracy of the ensemble classifier was calculated to be 85.00%, demonstrating its effectiveness in predicting stock market strategies.
