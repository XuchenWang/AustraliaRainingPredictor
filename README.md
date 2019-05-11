# Aussie Weather Forecast: Is it going to rain tomorrow?

*Using Bayesian models predicting whether it will rain tomorrow in Australia*

## Motivation
The development of human civilization has been highly depending on weather and climate. As early as the primitive society, precipitation played an irreplaceable role in agriculture and migration: it not only helped our ancestors to find out the best timing for sowing, but also determined where the next destination of the nomadic civilizations would be. Rainfall, as one of the major sources of freshwater, largely decided the survival rate of our ancestors. Today, people still care very much about weather and climate even though sowing seeds and nomadic life are away from our daily life. Numerous psychological studies have shown that pleasant weather is associated with better mood and memory. Other researchers suggest that sunny weather even boosts stock market returns. Moreover, for practical reasons, people need to know how to dress for the weather and whether they should bring an umbrella to work. As a result, correctly predicting the rainfalls is crucial in planning our schedule and improving life quality. Our research aims to create a prediction model for precipitation. When given sufficient information, our model is expected to output an accurate prediction on whether Australia is going to rain on the next day.

## Dataset
Our project aims to investigate and predict whether it will rain tomorrow by training a binary classification model. The original data are from the Bureau of Meteorology of Australia. The dataset was gathered by Joe Young in 2017. There are 142 thousand rows in the dataset, recording the weather observations in a ten-year period from October 2007 to January 2017. It contains daily weather observations from numerous Australian weather stations and the RainTomorrow binary indicator as a target. Below is a list of variables that we will use in our analysis: 

| Variable      | Description                                                                  | 
| ------------- |:----------------------------------------------------------------------------:|
| Rain Tomorrow | The target variable: Did it rain the next day of the observation?  Yes or No | 
| TempDiff      | The numerical difference between MaxTemp and MinTemp in Celsius              | 
| State         | The state where a town/city is located in Australia                          |
| City          | The city in Australia                                                        | 


## Models and Methodology

This paper mainly relies on Bayesian Statistics and the Logistic Classification method. To predict the probability of raining tomorrow, we build three primary models, along with the fourth model which is an improved version of Model 3. 

**Model 1: RainTomorrow~1**
*Assumption: Whether it rains tomorrow only depends on the overall raining rate.*

![](Model_Figure_1.png)

![Density plot of Rain_Tomorrow variable](Data_Figure_1.png)

We started with the simplest model, which counts the number of days that rain tomorrow in model 1. This diagram gives the general sense that most of the days in our dataset don’t rain on the next day. The number of days that rain tomorrow is around 30000 and the number of days that don’t rain tomorrow is around 110000. There are approximately 3.5 times days that don't rain tomorrow than the number of days that rain tomorrow.


**Model 2: RainTmr~TemDiff**
*Assumption: Whether it rains tomorrow only depends on the today's temperature difference.*

![](Model_Figure_2.png)

![Plot of Rain_Tomorrow and Tempreture_Difference](Data_Figure_2.png)

Then we incorporate the first covariate, the temperature difference, into model 2. This plot illustrates that if the temperature difference is below 8 degrees Celsius, it’s very likely to rain tomorrow. If the temperature difference is above 8 degrees Celsius, the probability of raining tomorrow would be low and it’s unlikely to rain. Since the area under both curves don’t have a lot of overlaps, our observations and conclusions above are relatively clear and convincing. 


**Model 3: RainTmr~ State+ TemDiff **
*whether it rains tomorrow depends on the raining rate in a specific state, each of which has a different trend with temperature difference.*

![](Model_Figure_3.png)

![Plot of Location and Tempreture_Difference](Data_Figure_3.png)

Then, we extend model 2 by adding the state variable into model 3. This plot gives an overview of the distribution of daily temperature differences in each state in Australia. We group all the cities into 8 states: New South Wales, Norfolk Island, Northern Australia, Queensland, South Australia,Tasmania, Victoria, Western Australia. From the plot, we observe that most of the states have similar distributions, where their temperature differences center around 10 degrees Celsius, with a relatively large spread/variance. Norfolk Island, Queensland, and Tasmania have rather different patterns. Norfolk Island’s mean temperature difference is 5 degrees Celsius and has relatively stable temperature during a day. Queensland’s mean temperature difference is 8 degrees Celsius with relatively small spread/variance. Tasmania’s mean temperature difference is 10 degrees Celsius with relatively small spread/variance, compare with the other common states. 

![Plot of Rain_Tomorrow, Location and Tempreture_Difference](Data_Figure_4.png)

Lastly, we graph the distribution of raining tomorrow and that of not raining tomorrow for each state/region, with respect to the temperature difference. The most obvious observations that we have is that, if New South Wales, Northern, Western, Southern Australia, Vistoria, or Tasmania has a temperature difference above 10 degrees Celsius, it's unlikely to rain tomorrow in that state;  if the  temperature difference is below 10 degrees Celsius, it's likely to rain tomorrow in that state. Queensland’s plot suggests a similar threshold at 8 degree Celsius. Norfolk Island is the most vague one, because the pink and blue area under the curves highly overlap with each other, making it hard to distinguish the threshold. Part of the reason is that the temperature difference on Norfolk Island is very small.  


**Model 4: RainTmr~ City + TemDiff **
*whether it rains tomorrow depends on the raining rate in a specific city, each of which has a different trend with temperature difference.*

![](Model_Figure_3.png)

![Plot of Location and Tempreture_Difference](Data_Figure_3.png)

This model is an improved version of Model 3 and replaces the state variable with the city variable, so that we can predict the weather for each city more precisely and make the model more practical for people to use in daily life. The above 6 plots present the distributions of raining tomorrow(blue) and not raining tomorrow(pink) for the top six cities with most data and presumably the most popular ones in Australia, with respect to today's temperature differences. The threshold for Brisbane, Darwin, Hobart, and Sydney is around 8 degrees Celsius, meaning that if today's temperature difference is below 8 degrees Celsius, tomorrow is likely to rain; Vice versa. The threshold of Perth is around 10 degrees Celsius, and that for Canberra is 12 degrees Celsius. Their thresholds are different, because these cities are located in different geographical areas. 












