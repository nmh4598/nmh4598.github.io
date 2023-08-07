## Modeling and forecasting the unemployment rate monthly in the United States

### Introduction

The unemployment rate is a crucial economic indicator for assessing the dynamism of the labor market. There are various causes for a high unemployment rate, including cyclical contractions in the economy or structural frictions in job search, such as stringent labor codes. The evolution of the unemployment rate is therefore vital for political and economic institutions, particularly the state and central banks, as it helps them make informed decisions regarding financial and monetary policies.

The United States of America's unemployment rate is particularly interesting due to its status as one of the largest markets in the world with relatively weak regulatory measures. Consequently, it maintains a low structural unemployment rate, typically hovering around 4.5%, indicating near full employment. In contrast, countries like France, which rank high in job protection, have experienced a consistently higher structural unemployment rate of approximately 8% over several decades.

As part of our project, we aimed to model the unemployment rate to provide month-by-month forecasts for the upcoming years. Our dataset consists of a monthly time series spanning from 1948 to 2023, tracking the changes in the unemployment rate in the United States.

### A history of unemployment in the united states

The raw time series we have poses two obstacles to effectively modeling the unemployment rate.

The first obstacle is the lengthy duration of the series, spanning seventy-five years. From a macroeconomic perspective, attempting to model an indicator like unemployment over such a long period is irrelevant. Demographics, technological progress, productivity, and the global political and economic landscape have undergone significant transformations in less than a century, bearing little resemblance to what they were in 1948. Considering this reality, we have chosen to reduce the duration of the series by starting it in 1989. This year marks the fall of the Berlin Wall, symbolizing the collapse of the Soviet bloc and the end of the Cold War. It signifies the transition from a bipolar world to a relatively stable unipolar world, with the United States as the leading global power.

The second obstacle is related to the COVID-19 pandemic that struck the world in 2020. The lockdown measures implemented in response to this unprecedented health crisis resulted in a significant surge in the unemployment rate, soaring from around 3.5% in February 2020 to 14.7% in April 2022—an unprecedented level in the United States since the Great Depression. The rate gradually declined and returned to its pre-pandemic level by early 2022. Since this event was unforeseeable and beyond economic and financial considerations, we have chosen to disregard it. Consequently, the models we have developed are based on a truncated version of the time series, ending in December 2019.

However, the forecasts derived from the selected model will be performed on the 1989 series, encompassing the period up until the present, including the impact of the health crisis. Therefore, our analysis will be based on the monthly evolution of the unemployment rate over a thirty-year period, ranging from 1989 to 2019.

### Modeling unemployement: ARIMA, ARIMAX, LSTAR

We built three different models. Two of these models are linear – the ARIMA and ARIMAX models – while the third is nonlinear – the LSTAR model.
The idea was to compare these three models using several indicators and retain the one whose intra-project forecasts sample were the most relevant.
=== "ARIMA"
    The initial model used is the ARMA model (Autoregressive Moving Average). The concept behind this model is to represent the analyzed time series as a combination of its past random error values and terms, assuming linearity. However, since the series being analyzed is not stationary, the ARIMA model (Autoregressive Integrated Moving Average) is employed. The "I" in ARIMA stands for Integrated, indicating that the model considers the differences between observations in the time series rather than the raw values, allowing for the treatment of a non-stationary series.

    The selection of an ARIMA model is justified by the fact that the unemployment rate is typically highly correlated with its past values. If unemployment increases in March, it is highly probable that it will continue to increase in April of the same year, and vice versa. Based on this assumption, without incorporating any exogenous variables at this stage, we have modeled unemployment.

    In this case, the chosen ARIMA model is as follows: ARIMA (1, 1, 3) (1, 0, 2). The Ljung-Box test yields a p-value of 0.71, well above the threshold α of 0.05. This indicates  that the null hypothesis is not rejected, meaning that the residuals of our model are independent and not autocorrelated, indicating good model quality.

    To evaluate the performance of our model, we have conducted within-sample predictions. We selected an arbitrary date, denoted as T*, which corresponds to December of the year  2014. This allows us to compare the model's predictions with the actual values. For this model and subsequent ones, we calculated the root-mean-square error (RMSE) for forecast horizons of h = 1 and h = 5, representing one month and five months into the future, respectively. Additionally, we computed the Theil U statistic for horizons of h = 1 and h = 4, ie one month and four months later. Its expression is as follows: U = $\frac{RMSE selected model}{RMSE naive model}$
=== "ARIMAX"

=== "LSTAR"