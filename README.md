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
  <img width="640" height="480" alt="feature_importance" src="https://github.com/user-attachments/assets/4dc97e12-140e-40bd-a9fa-f3a1ab4494e3" />
</p>


10. Click "Download Forecast and Plots"
The user is able to download the data


11. Click "Download Log"
The user is able to log from the system


11. Click "Clear Log"
The user can clear anything from the log



