# 2024_ia651_velagapudi

# Seoul Bike Sharing System Dataset

## Overview

The dataset contains count of public bicycles rented per hour in the Seoul Bike Sharing System, with corresponding weather data and holiday information

This dataset is taken from uci machine learning repository
https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand

## Dataset Details

The dataset includes the following features:

- **Rented Bike Count**: The number of bikes rented per hour.
- **Weather Information**:
  - **Temperature**: Temperature in degrees Celsius.
  - **Humidity**: Relative humidity percentage.
  - **Windspeed**: Wind speed in meters per second.
  - **Visibility**: Visibility in meters.
  - **Dewpoint**: Dewpoint temperature in degrees Celsius.
  - **Solar Radiation**: Solar radiation in watts per square meter.
  - **Snowfall**: Snowfall amount in millimeters.
  - **Rainfall**: Rainfall amount in millimeters.
- **Date Information**:
  - **Date**: year-month-day
  - **Hour**: Hour of he day
- **Holiday**: Information on whether the date is a holiday.(Holiday/No holiday)
- **Functioning Day** - Information on whether the date is a Fucntioning Day.(Yes/No)
- **Number of Instances**: 8760

The dataset has no missing values

## Objectives

Currently Rental bikes are introduced in many urban cities for the enhancement of mobility comfort. It is important to make the rental bike available and accessible to the public at the right time as it lessens the waiting time. Eventually, providing the city with a stable supply of rental bikes becomes a major concern. The crucial part is the prediction of bike count required at each hour for the stable supply of rental bikes. 

This project aims to predict Rented Bike Count variable based on several input features

Random forest regression model will be built as other regression techniques such as Linear regression will fail to capture nonlinear relationships and the amount data might not be enough for training neural entworks. Random forests are popular and do well in multivariate regression and are less likely to overfit as the final prediction is average prediction of multiple trees

## Exploratory Data Analysis EDA
Sample Data
![Screenshot 2024-07-20 162126](https://github.com/user-attachments/assets/0c589275-a21e-4fb8-b211-70f111af66d7)

Data is split into train and test sets with test size of 0.2 and random state of 42\
Only training data is used in exploratory data analysis to avoid data leakage\
Year and Weekday are extracted from datetime column

### Distribution of features
Numerical Features
![0](https://github.com/user-attachments/assets/9322e140-ffa5-4712-b0a6-c08aabd54164)

Categorical Features
![1](https://github.com/user-attachments/assets/6f621111-8805-497e-947d-8605d06a3121)

### Correlation Matrix
![Screenshot 2024-07-20 161446](https://github.com/user-attachments/assets/9fbda2b0-d3c9-40c0-b762-00e579b47e42)

### Exploratory Stats
Average Rented Bike Count by Season and Holiday
![Screenshot 2024-07-20 161508](https://github.com/user-attachments/assets/7860d35b-73fa-47e3-aba0-5c11bbb79529)

Average Rented Bike Count by Hour
![Screenshot 2024-07-20 161542](https://github.com/user-attachments/assets/31c45433-c039-44e7-8c0c-1a4564c6b0b6)

Average Rented Bike Count by Functioning Day

![Screenshot 2024-07-20 161522](https://github.com/user-attachments/assets/cc111beb-d443-49d6-90b2-6901686ca07a)
As average rented bike count is 0 for non functioning days The model will be adjusted to predict 0 everytime functioning day is 0

Average Rented Bike Count by Holiday

![Screenshot 2024-07-20 161530](https://github.com/user-attachments/assets/b7624748-659d-4cf0-81de-c1a1dca9204e)

Mean rented bike count by year

![Screenshot 2024-07-20 161641](https://github.com/user-attachments/assets/f7f81687-a741-4b6f-ae27-3133a450fa7f)

Mean(average of middle 50% values to avoid outliers) rented bike count by year

![Screenshot 2024-07-20 161652](https://github.com/user-attachments/assets/308ab0dc-457b-4b9e-b9b2-60f67a0ec010)

Mean rented bike count by weekday

![Screenshot 2024-07-20 161702](https://github.com/user-attachments/assets/93fd6db3-3d6e-4e18-b4e4-d295e2d0c6ef)

## Feature selection -
All numerical features are selected as they are well correlated with the target variable(Rented Bike Count) as all absolute correlation values are 0.1 and greater

All categorical columns(Functioning day,Holiday,Season) are also selected as they are significantly impacting(from EDA above there is significant variation in Rented Bike Count for different values of these categorical variables) Rented Bike Count.

Hour is signifcantly impacting Rented Bike Count (see Hour vs Rented Bike Count plot) and It has positive correlation of 0.42 with Rented Bike Count(see Correlation matrix) indicating increasing trend on average as hour of the day increases and Daily routines often vary by hour, making it an important factor to consider.

Year is included as there is significant difference in Mean Rented Bike Count by Year. Note that the model will be trained only on 2017 and 2018 data when a new year is introduced the model cant make reliable predictions; a solution for that is suggested at the end.

Weekday is included as there is substantial difference in Mean Rented Bike Count by Weekday and it could be a required factor as weekly routines are common.

Date and Month are not included to avoid turning it into a time series model as Random forest can't handle time series data well enough and to focus to building a simple more generalized model based on non datetime input features, Hour and weekday are included to capture very common obvious routines. 

## Feature engineering -
Categorical variables Functioning day and Holiday are numerically encoded as they are binary categorical variables\
Season and Weekday are label encoded numerically for the following reasons

1.One Hot encoding is not suitable for Random Forest Model as it increases tree complexity which could be more prone to making bad predictions.\
2.Tree models handle numerical label encoding as they can make very precise splits.

Weekday- {'Monday': 1, 'Tuesday': 2, 'Wednesday': 3, 'Thursday': 4, 'Friday': 5, 'Saturday': 6, 'Sunday': 7}\
Holiday- {'Holiday': 0, 'No Holiday': 1}\
Functioning day- {'Yes': 1, 'No': 0}\
Seasons- {
    'Autumn': 0,
    'Spring': 1,
    'Summer': 2,
    'Winter': 3
}\
Hour is already label encoded


Data After Feature Engineering
![Screenshot 2024-07-20 162155](https://github.com/user-attachments/assets/27c0f6b7-4c39-46e8-9687-ea9d36e65419)

## Final Model
A Random Forest model with parameters n_estimators=100,bootstrap=True is trained on trainset and tested on testset

Results

![Screenshot 2024-07-20 181534](https://github.com/user-attachments/assets/a59a7724-647a-470d-8b81-394af1216502)

Performance on trainset

![Screenshot 2024-07-20 175738](https://github.com/user-attachments/assets/97d0c7d2-9e3c-4e7f-b836-fdbf3fb14578)

Prediction examples 

Test example 1:\
Input features:\
{'Hour': 8.0, 'Temperature(°C)': 27.2, 'Humidity(%)': 69.0, 'Wind speed (m/s)': 1.8, 'Visibility (10m)': 1999.0, 'Dew point temperature(°C)': 21.0, 'Solar Radiation (MJ/m2)': 0.7, 'Rainfall(mm)': 0.0, 'Snowfall (cm)': 0.0, 'Seasons': 2.0, 'Holiday': 1.0, 'Functioning Day': 1.0, 'Year': 2018.0, 'WeekDay': 5.0}\
Actual: 1728\
Predicted: 779.1\

Test example 2:\
Input features:\
{'Hour': 12.0, 'Temperature(°C)': 32.6, 'Humidity(%)': 51.0, 'Wind speed (m/s)': 2.1, 'Visibility (10m)': 800.0, 'Dew point temperature(°C)': 21.1, 'Solar Radiation (MJ/m2)': 3.21, 'Rainfall(mm)': 0.0, 'Snowfall (cm)': 0.0, 'Seasons': 2.0, 'Holiday': 1.0, 'Functioning Day': 1.0, 'Year': 2018.0, 'WeekDay': 5.0}\
Actual: 822\
Predicted: 1057.86

Synthesized example 1:\
Input features:\
{'Hour': 10.0, 'Temperature(°C)': 25.0, 'Humidity(%)': 40.0, 'Wind speed (m/s)': 2.0, 'Visibility (10m)': 2000.0, 'Dew point temperature(°C)': 15.0, 'Solar Radiation (MJ/m2)': 0.5, 'Rainfall(mm)': 0.0, 'Snowfall (cm)': 0.0, 'Seasons': 0.0, 'Holiday': 1.0, 'Functioning Day': 1.0, 'Year': 2017.0, 'WeekDay': 1.0}\
Predicted: 857.84

Synthesized example 2:\
Input features:\
{'Hour': 14.0, 'Temperature(°C)': 30.0, 'Humidity(%)': 50.0, 'Wind speed (m/s)': 3.5, 'Visibility (10m)': 1500.0, 'Dew point temperature(°C)': 20.0, 'Solar Radiation (MJ/m2)': 0.1, 'Rainfall(mm)': 0.1, 'Snowfall (cm)': 0.1, 'Seasons': 3.0, 'Holiday': 1.0, 'Functioning Day': 1.0, 'Year': 2017.0, 'WeekDay': 7.0}\
Predicted: 391.5


Random forests are usually less prone to overfitting and do not require extensive hyperparameter tuning

Note that random forest model could give slightly different results every time it's trained because of bootstrapping(training on random subsets of training data) but its only a slight difference.

## Limitations
This Model is Statistical and cannot make exact predictions.\
Random Forest models are not easily interpretable compared to single decision trees.\
This model can give far off predictions as seen in the test example 1 especially with outliers.\
This model is only trained on 2017 and 2018 year data; could give bad predictions for newer years.\
The model cannot forecast unanticipated events for which it is not trained on.


## Production
This model is only trained on 2017 and 2018 year data(year variable has only these two values in training data) so it cant make prediction for newer years.

To make predictions on newer data; metrics like year over year growth or monthly growth in Rented Bikes (forecasted and otherwise) could be incorporated and the final predictions from random forest model could be adjusted based on those metrics.

Model could be further improved by increasing number of datapoints, selecting other relevant variables based on domain knowledge such as Traffic data, Geographic data etc. 



