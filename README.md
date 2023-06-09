# Fixed-Income-Quantitative-Trading
Data:
Eurodollar futures prices downloaded from Quandl. There are 20 time series in the dataset. We are going to assume that 8th series corresponds to 2y maturity, 12th corresponds to 3y, 16th to 4yr and 20th contract corresponds to 5y maturity. 
Compute futures rates from futures prices (100-price), and use them in the analysis.

Historical samples:
- 1/1/2010 through 1/1/2014, Estimation Sample (A) 
- 1/1/2014 through 1/1/2016 Signal Building Sample (B) 
- 1/1/2016 through 1/1/2018, Testing Sample (C)

1. Use Sample A to compute 3 cointegrated butterflies of ED futures rates:[2y,3y,5y],[3y,4y,5y], [2y,3y,4y]. Weight on the belly of a butterlfy is 1 for all combinations.

2. Let's define z(t,lambda) as {x(t) - EMA(x(t); lambda)} where x(t) is a cointegrated butterfly at t. Use Sample B to construct the following forecasting models:
a. AR(1) model fitted to z(t,lambda = 0) (Signal 1), this is a constant mean case 
b. AR(1) model fitted to z(t,lambda = 0.05) (Signal 2)
c. AR(1) model fitted to z(t,lambda = 0.1) (Signal 3)

Each model is estimated in a rolling 6m window, and forecast, E[z(t+H)|t], is produced for H=5 days. 
Note that the forecast for the cointegrated butterffly at t+H will be E[z(t+H)|t]+EMA(t,lambda) (we assume that EMA value won't change in H days).

3. Suggest a method of combining Signals 1, 2 & 3. Call the combination (or mixture of signals) Signal 4.

4. Define one or two signal quality metrics, and explain clearly what method I am implementing.
