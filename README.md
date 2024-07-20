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
### Distribution of features
Numerical Features
![0](https://github.com/user-attachments/assets/9322e140-ffa5-4712-b0a6-c08aabd54164)

Categorical Features
![1](https://github.com/user-attachments/assets/6f621111-8805-497e-947d-8605d06a3121)

