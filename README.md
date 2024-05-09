# Lake Effect Precipitation Prediction

# CNN & RNN-LSTM HYBRID DEEP LEARNING MODEL

# Introduction
In this project, I explore a hybrid deep learning model combining Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) to predict lake effect precipitation One, Two, and Three days in advance. This advanced model architecture leverages both image and sequential data to enhance predictive performance.

# Data Description

## Satellite Data

### Source
The satellite data primarily comes from geostationary satellites, specifically the GOES (Geostationary Operational Environmental Satellites). These satellites are positioned to provide a constant watch over the same geographic area, allowing for continuous monitoring of atmospheric conditions.

### Content
The satellite data includes high-resolution imagery. This imagery is instrumental in observing cloud formations over Lake Michigan. These details are essential for understanding and predicting weather patterns to lake effect precipitation.

## Weather Station Data

### Source
This data is sourced from ground-based weather stations strategically located near the lakeshore of Lake Michigan. These stations are ideally placed to capture detailed local atmospheric conditions that satellite imagery might miss.

### Content
Meteorological Data from Weather Stations
- **Temp (F)**: Air temperature in degrees Fahrenheit at the time of observation.
- **RH (%)**: Relative humidity percentage, indicating the amount of moisture in the air.
- **Dewpt (F)**: Dew point temperature in Fahrenheit, which is the temperature to which air must be cooled to become saturated with water vapor.
- **Wind Spd (mph)**: Wind speed measured in miles per hour.
- **Wind Direction (deg)**: The direction from which the wind is blowing, in degrees from true north.
- **Peak Wind Gust(mph)**: The highest speed of wind gusts during the hour, in miles per hour.
- **Low/Med/High Cloud Ht (ft)**: The height of the lowest, middle, and highest cloud layers above the ground, in feet.
- **Visibility (mi)**: The maximum distance at which objects can be clearly seen, in miles.
- **Atm Press (hPa), Sea Lev Press (hPa), Altimeter (hPa)**: Atmospheric pressure at the station level, sea level pressure, and pressure reading from an altimeter, all in hectopascals.
- **Precip (in)**: The amount of precipitation in inches during the hour.
- **Wind Chill (F)**: The perceived decrease in air temperature felt by the body due to the flow of air.
- **Heat Index (F)**: An index that combines air temperature and relative humidity to determine an apparent temperature—how hot it feels.

# 2. Data Preprocessing
### 1. Data Preprocessing and Exploratory Data Analysis (EDA)
- **Data Cleaning**: Features are renamed for clarity, date and time columns are combined into a single column focused on UTC time, and missing or non-numerical values are handled efficiently.
- **Feature Engineering**: Removed features with a high percentage of missing values and highly correlated features to reduce redundancy and improve model accuracy.
- **Temporal Data Handling**: Data is sorted chronologically.
- **Data imputation**: Implemented data imputation strategies and data type conversions to prepare the dataset for modeling.

### 2. Image Analysis
- **Satellite Image Processing**: Analyzed and processed satellite images, removing those with poor lighting or distortion, focusing on clear images available between 14:00 and 22:00 UTC.
- **Data Filtration**: Filter image data based on sunlight availability and image clarity to enhance data quality for CNN modeling.

### 3. Data Saving and Organization
- **File Management**: Data is organized into different files tailored for specific parts of the analysis:
  - `les_data.csv` - Contains all processed features.
  - `meteorological_data.csv` - Dedicated to meteorological features for RNN processing.
  - `filtered_les_cld_imgs.csv` - Includes DateTime_UTC and lake_data_2D columns for CNN processing.

# 3. Visualizations
### 1. Yearly and Monthly Precipitation Analysis
- **Total Yearly Precipitation**: Plots the total precipitation for each year to observe trends over time.
- **Aggregated Monthly Precipitation**: For each year, a detailed monthly precipitation plot shows the distribution and trends within the year.
- **Monthly Observations Scatter Plot**: Provides a scatter plot for daily observations within each month, across all years, to visualize variability and outliers.

### 2. Time Series Analysis
- **Time Series Precipitation Plot**: A continuous plot showing the precipitation over time, highlighting any seasonal patterns or anomalies.

### 3. Detailed Feature Relationships
- **Pair Plots**: Visualize relationships between all features in the dataset to understand correlations and potential predictive relationships.
- **Relationship Plots**: Specific plots between each feature and precipitation to highlight how different meteorological conditions may influence precipitation patterns.

### 4. Correlation Analysis
- **Autocorrelation Plot**: Analyzes the correlation of precipitation with its past values to identify persistence or seasonality up to 30 days.
- **Partial Autocorrelation Plot**: Provides insights into direct relationships between precipitation on different days, controlling for the values at intervening days.
