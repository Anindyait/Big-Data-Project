# Spatio-Temporal Analysis on COVID-19 cases

## Literature Review
Selected Papers for Replication.
Based on the use-case we have majorly focused on the following 2 Research papers.

1. ***Tracking and Forecasting Milepost Moments of the Epidemic in the Early-Outbreak: Framework and Applications to the COVID-19***


        Overview: Proposes a framework to identify critical points ("milepost moments") in the early stages of an epidemic using indicators like infection rate velocity and removal rate velocity.

        Source: PMC7737706

2. ***Geospatial Modeling to Assess the Impact of Mobility Restrictions on COVID-19 Spread***


        Overview: Utilizes geospatial analysis to evaluate how mobility restrictions influence the spread of COVID-19, emphasizing the importance of spatial factors in epidemic modeling.

        Source: Tandfonline


## Replication Plan

Raw dataset - https://www.kaggle.com/code/eswarchandt/geospatial-analysis-on-covid-19-day-to-day-track/notebook

Cleaned dataset  [```covid_19_data.csv```](/covid_19_data.csv)

### 1. Data Preprocessing

> **Objective**: Prepare the dataset for analysis by ensuring consistency and completeness.

Actions:

    1.1 Convert the Date column to datetime format.

    1.2 Handled missing values in Province/State by filling with appropriate placeholders or aggregating data at the country level.

    1.3 Ensure numerical columns (Confirmed, Deaths, Recovered, Active) are of integer type.

    1.4 Derived Feature Columns Added (Active Ratio & Fatality Rate)

---

### 2. Identifying Milepost Moments (Based on PMC7737706)

> **Objective**: Detect significant changes in the epidemic curve.

Actions:

        2.1 Calculate daily new cases by computing the difference in Confirmed cases day-over-day.

        2.2 Compute infection active cases and recovered cases to identify turning points in the epidemic's progression.

        2.3 Visualize these metrics to pinpoint critical moments in the outbreak.

---

### 3. Geospatial Analysis of Mobility Restrictions (Based on Tandfonline Paper)

> **Objective**: Assess the spatial impact of mobility restrictions on COVID-19 spread.

Actions:

        3.1 Map the Lat and Long data to visualize the geographical distribution of cases.

        3.2 Overlay simulated mobility restriction data to examine correlations between movement limitations and case numbers.

        3.3 Use geospatial statistical methods to quantify the impact of mobility restrictions.
        
---

### 4. Forecasting Future Trends

> **Objective**: Predict future case numbers using time series forecasting methods.

Actions:

        4.1 Implement forecasting models such as ARIMA, SARIMA & CNN-LSTM on the Confirmed cases time series.

        4.2 Evaluate model performance using metrics like MAE or MAPE.

        4.3 Visualize forecasted trends alongside actual data for comparison.

<br>

**4.1. Temporal Model - Global Comparison**
```
Model     | Confirmed Cases(MAE, MAPE) | Death Cases(MAE, MAPE)
__________|____________________________|_______________________
          |                            |                  
ARIMA	  |       190.6k, 1.26%        |    4.6k, 0.74%
__________|____________________________|_______________________
          |                            |                    
SARIMA	  |        129k,0.85%          |    1.1k, 0.19%
__________|____________________________|_______________________
          |                            |         
LSTM	  |        19.8k,0.35%         |    1.9k, 0.31%
__________|____________________________|_______________________
```

**4.2. Temporal Model - Country-Wise (Canada)**
```
Model     | Confirmed Cases(MAE, MAPE) | Death Cases(MAE, MAPE)
__________|____________________________|_______________________
          |                            |                  
ARIMA	  |      1,037.15, 0.91%       |   61.21, 0.69%
__________|____________________________|_______________________
          |                            |
SARIMA	  |      1,037.15, 0.91%       |   61.21, 0.69%
__________|____________________________|_______________________
          |                            |                     
LSTM	  |       572.84, 0.50%        |    7.82, 0.09%
__________|____________________________|_______________________
```

**4.3. Spatio-Temporal Model**
```
Model     | Confirmed Cases(MAE, MSE)  | Death Cases(MAE, MSE)
__________|____________________________|_______________________
          |                            |                   
CNN-LSTM  |      0.0182, 0.0053        |    0.0121, 0.0025
__________|____________________________|_______________________
```






## 5. Future Scope

While the current model effectively captures spatio-temporal patterns in country-level COVID-19 data, there is significant scope for improvement. 

1. **Incorporating higher spatial resolution data**, such as information down to the district or city level, would enable more fine-grained forecasting and localized policy interventions.

2. **Integrating real-time data streams** (e.g., from APIs or live dashboards) could allow the model to adapt to evolving outbreak dynamics, improving its responsiveness and accuracy. Future versions of this model could also explore multimodal inputs like mobility data, climate conditions, or healthcare infrastructure, enriching the temporal context and boosting predictive performance.
















