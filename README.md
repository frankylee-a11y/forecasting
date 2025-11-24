Usage guide 

<img width="997" height="825" alt="Capture" src="https://github.com/user-attachments/assets/ebdccd6f-fd3c-4836-a51d-24b233571a42" />

Using the snapshot shown above, follow the steps shown below,
1. Click "Load CSV"
Select the daily sales file (must include columns: Date, Sales, Open)


2. Click "Process Data"
Cleans missing values
Encodes date features
Creates lag variables

3. Click "Train Model"
Trains the linear regression model using an 80/20 time-series split

4. Click "Forecast Test Data"
Allows the user to choose how much data points they would like to forecast.
Limitations include that the forecast must be the size of 20% of the data set provided. An example of the forecasted results can be shown below.

<p align="center">
  <img width="160" height="579" alt="New_Capture" src="https://github.com/user-attachments/assets/5071a2a3-4015-45a1-8b68-332b0937db28" />
</p>

5. Click "Plot Actual vs Predicted"
Uses the code plot_actual_vs_pred showing how close predictions follow the real data. The figure is shown below. The true sales in blue with the model's predictions in green are compared over the test period. The peaks are sometimes under-preducted and troughs sometimes overpredicted as can be expected of linear regression struggling with extreme values.  
<p align="center">
  <img width="640" height="480" alt="actual_vs_predicted" src="https://github.com/user-attachments/assets/81b1028e-5eb8-4c14-99d2-89961b96255a" />
</p>
7. Click "Plot Residuals"
From the plot_residuals code, the figure below shows the error size across the test period. It is basically the difference between the actual and predicted sales (Residual = Actual - Predicted)  resulting in error across time.  The residuals that bounce around the zero y-axis indicate no obvious bias as shown in the graph. The large negative dips means that the model is unable to capture the sudden sales spikes (as can be predicted for linear models). 
<p align="center">
  <img width="640" height="480" alt="residuals" src="https://github.com/user-attachments/assets/adf1f0e6-e918-4836-bebd-1424a724ca54" />
</p>


8. Click "Plot Error Histogram"
From the code plot_error_hist, the distribution of prediction error is displayed in the histogram figure below. Errors center around the 0 to +1000 area, meaning that the model slightly overpredicts on average. The distribution is roughly bell-shaped but is skewed showing more moderate outliers than extreme errors. Our histogram displays a wider spread that is consistent with the MAE ~1000 and RMSE ~1500. 
<p align="center">
  <img width="640" height="480" alt="error_histogram" src="https://github.com/user-attachments/assets/275f42ce-b952-434b-863c-3fad8167c3db" />
</p>


9. Click "Plot Feature Imporatance"
From the code plot_feature_importance, the image below shows the lag and the dummy month's features and which of them influences the model most. The bar lengths indicate the absolute value of each model coefficient and how strongly it impacts the prediction. The lagged sales (Sales_lag1,lag2,lag3) have almost contributed nothing as can be seen from the chart. On the other hand, promo is a dominant driver of the predicted sales, indicating that promos heavily increase the expected revenue. The months also play a significant role in the sales number, as the December (month 12) and August (month 8) have the strongest effects - can be attributed to the holidays seasons and the “Back-to-School” seasons. Lastly, the Day of week patterns matters as certain days may have higher sales than baseline sales (i.e. weekend vs weekdays). The model partially depends on the weekly seasonality. 
<p align="center">
<img width="640" height="480" alt="feature_importance" src="https://github.com/user-attachments/assets/be656f84-5694-424e-b5a7-57368686b8fb" />
</p>


10. Click "Download Forecast and Plots"
The user is able to download the data


11. Click "Download Log"
The user is able to log from the system


11. Click "Clear Log"
The user can clear anything from the log

Summary of development of python-based Sales Data Forecasting and Analysis system,

This report presents the design, development, and evaluation of a Python-based Sales Data Forecasting and Analysis System built with a PyQt5 GUI. The system enables users to load sales data, preprocess it, train machine learning models, test model performance, generate forecasts, visualize results, and export outputs. The purpose is to help retail operations make informed decisions based on historical and predicted sales trends.

System Overview
The system contains several modular components:

1.ForecastGUI: Handles user interaction, file loading, model operations, and visualizations.

2.DataProcessor: Cleans and prepares data by removing closed days, handling missing values, creating lag features, and encoding date attributes.

3.ForecastingModel: Implements two forecasting approaches — Linear Regression (main) and Random Forest Classifier (alternative).

4.ResultsVisualizer: Generates graphs such as actual vs predicted plots, residual analysis, error histograms, and feature importance charts.

5.Logger: Records all system actions and errors for transparency and debugging.

Methodology

The methodology consists of five parts:

1.Data Loading & Preprocessing:
The system validates the file, removes closed-store dates, fills missing values with zeros, creates lag features, and encodes categorical variables like months and days. No normalization was required since features are already in numeric or binary form.

2.Model Selection & Training:
Two models were compared:

Linear Regression: Predicts numeric sales values and captures general trends. Random Forest Classifier: Included for experimentation but better suited for classification, not numeric forecasting.An 80/20 time-series split was used for training/testing.

3.Testing:
Models were evaluated using:
Mean Absolute Error (MAE)
Root Mean Squared Error (RMSE)
R² score

4.Model Comparison:
Linear Regression outperformed Random Forest significantly:
LR R² ≈ 0.65
RF R² ≈ –0.01
Random Forest misinterpreted numeric forecasting as classification, leading to poor performance.

5.Multi-Step Forecasting:
The system allows users to forecast multiple future periods, generating results that can be exported and plotted.

Results

Key findings include:
1.Model Accuracy:
LR captured 63–65% of sales variance, showing stable generalization without overfitting.

2.Performance Metrics:

MAE ≈ 1000 units

RMSE ≈ 1500 units

Forecasted vs Actual Trends:
The model captures overall seasonality and patterns but struggles with extreme spikes during holidays or promotions.

3.Visualizations:

Actual vs Predicted plots show good general trend matching.
Residuals fluctuate around zero, indicating no major biases.
Error histogram suggests slight overprediction.
Feature importance shows promotion and month variables strongly influence sales, while lag features contribute little.

4.Error Handling

The system includes robust exception handling for:
Missing files
Invalid or improperly formatted CSVs
Missing required columns
Training/testing performed out of sequence
Attempting to export before forecasting
Errors are shown to the user and logged automatically.

5.System Evaluation

Performance: Acceptable for local processing but limited by in-memory operations.
User Interface: Simple and intuitive with sequential workflow and clear feedback messages.

Limitations: No hyperparameter optimization,Not suitable for very large datasets,Linear model cannot capture non-linear patterns or extreme spikes ,GUI cannot run in cloud environments like Google Colab

Conclusion

The project successfully developed a functional forecasting and analysis system that transforms raw retail sales data into meaningful insights. The Linear Regression model demonstrated moderate accuracy and stability. Future improvements include implementing more advanced time-series models, improving seasonality handling, expanding forecast capabilities, and enhancing scalability.





