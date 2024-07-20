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
- **Functionining Day** - Information on whether the date is a Fucntioning Day.(Yes/No)
- **Number of Instances**: [Specify the exact number of rows/instances in your dataset]

The dataset has no missing values

## Objectives

Currently Rental bikes are introduced in many urban cities for the enhancement of mobility comfort. It is important to make the rental bike available and accessible to the public at the right time as it lessens the waiting time. Eventually, providing the city with a stable supply of rental bikes becomes a major concern. The crucial part is the prediction of bike count required at each hour for the stable supply of rental bikes. 

This project aims to predict Rented Bike Count variable based on several input features

## Exploratory Data Analysis EDA
Sample Data
![Screenshot 2024-07-20 162126](https://github.com/user-attachments/assets/0c589275-a21e-4fb8-b211-70f111af66d7)

Data is split into train and test sets with test size of 0.2 and random state of 42
Only training data is used in exploratory data analysis to avoid data leakage

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

Average Rented Bike Count by Holiday

![Screenshot 2024-07-20 161530](https://github.com/user-attachments/assets/b7624748-659d-4cf0-81de-c1a1dca9204e)

Mean rented bike count by year
![Screenshot 2024-07-20 161641](https://github.com/user-attachments/assets/f7f81687-a741-4b6f-ae27-3133a450fa7f)

Mean(average of middle 50% values to avoid outliers) rented bike count by year
![Screenshot 2024-07-20 161652](https://github.com/user-attachments/assets/308ab0dc-457b-4b9e-b9b2-60f67a0ec010)

Mean rented bike count by weekday
![Screenshot 2024-07-20 161702](https://github.com/user-attachments/assets/93fd6db3-3d6e-4e18-b4e4-d295e2d0c6ef)

Data After Encoding Categorical Variables
![Screenshot 2024-07-20 162155](https://github.com/user-attachments/assets/27c0f6b7-4c39-46e8-9687-ea9d36e65419)

Results
![Screenshot 2024-07-20 162219](https://github.com/user-attachments/assets/0b339970-45f2-4f89-aae6-827999d989b6)
