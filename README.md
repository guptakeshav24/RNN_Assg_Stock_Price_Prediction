This notebook aimed to predict the stock prices of four technology companies (IBM, Google, Amazon, and Microsoft) using historical data and Recurrent Neural Networks (RNNs).

**Data Preparation:**
- Historical stock data for each company was loaded from CSV files.
- The dataframes were merged horizontally based on the 'Date' column, and columns were renamed for clarity.
- A single row with missing values was identified and dropped from the combined dataset.

**Analysis and Visualization:**
- The frequency distribution of stock volumes for each company was analyzed, showing a skew towards lower trading volumes with occasional high volume outliers, particularly for MSFT.
- Correlation analysis revealed high correlations between the 'Open', 'High', 'Low', and 'Close' prices within each stock, and also strong correlations between the price movements of the different technology stocks.

**Data Processing for RNNs:**
- The combined data was prepared for RNN models by creating windowed sequences of features (X) and corresponding target values (y) using a window size of 21 days, based on observations from plotting data with different window sizes. A stride of 1 was used for creating the windows.
- The data was scaled using `MinMaxScaler` with `partial_fit` to avoid data leakage.
- The scaled data was split into training, validation, and testing sets.

**RNN Model Development and Evaluation:**
- Simple RNN and LSTM models were built and evaluated for stock price prediction.
- Hyperparameter tuning was performed for both model types by varying the number of hidden layers, dropout rates, and the number of dense layers.
- The optimal configurations were determined based on the lowest Mean Squared Error (MSE) on the validation set during training.

**Optimal Model Configurations and Performance:**
- **Simple RNN:** The optimal configuration was found to be 3 SimpleRNN layers, 0.1 dropout, and 1 dense layer. The R-squared score on the test set was approximately 0.9598 and an adjusted R-squared of 0.96 on the test set, with a Mean Squared Error of 5.56e-05. .
- **LSTM:** The optimal configuration was found to be 1 LSTM layer, 0 dropout, and 1 dense layer. This model achieved an R-squared score of approximately 0.9905 and an adjusted R-squared of 0.99 on the test set, with a Mean Squared Error of 8.06e-05.

**Insights:**
- The high R-squared and adjusted R-squared values for both models, particularly the LSTM, indicate that the models are performing well in predicting stock prices based on the historical data provided.
- The low MSE values further support the accuracy of the predictions.
- The analysis of windowed data suggested that a window size of 21 or 63 days captures relevant patterns for prediction.
- The strong correlations between the technology stocks suggest that using combined data from multiple companies is beneficial for capturing broader market trends.

**Further Improvements:**
- Further tuning of hyperparameters, including learning rates and optimizer choices, could potentially improve model performance.
- Incorporating additional features such as technical indicators or sentiment analysis could enhance prediction accuracy.
- Exploring more complex RNN architectures like Bidirectional LSTMs or GRUs might yield better results.
