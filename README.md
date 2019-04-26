# AustraliaRainingPredictor
Using Bayesian models predicting whether it will rain tomorrow in Australia

Our project aims to investigate and predict whether it will rain tomorrow by training a binary classification model. The original data are from the Bureau of Meteorology of Australia. The dataset was gathered by Joe Young in 2017. There are 142 thousand rows in the dataset, recording the weather observations in a ten-year period from October 2007 to January 2017. It contains daily weather observations from numerous Australian weather stations and the RainTomorrow binary indicator as a target. 

**Model 1**
$$
\begin{split}  
Y_{i} | \theta, b_0& \sim  Bern(\theta) \\ 
log(\frac{\theta}{1-\theta})  & = b_0 \\
b_0 & \sim N(0.3, \frac{1}{2500})
\end{split}
$$
