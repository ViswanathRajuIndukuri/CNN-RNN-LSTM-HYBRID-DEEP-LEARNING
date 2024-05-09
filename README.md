# Lake Effect Precipitation Prediction

# Hybrid CNN & RNN-LSTM Deep Learning Model

# Introduction
In this project, I've developed a hybrid deep learning model combining Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) to predict precipitation whether it will be No Rain, Light Rain, Moderate Rain and Heavy Rain for One, Two, and Three days in advance. This advanced model architecture leverages both sequential cloud images and meteorological data to enhance predictive performance.

# Data Description

### Satellite Data

#### Source:
The satellite data primarily comes from geostationary satellites, specifically the GOES (Geostationary Operational Environmental Satellites). These satellites are positioned to provide a constant watch over the same geographic area, allowing for continuous monitoring of atmospheric conditions.

#### Content:
The satellite data includes high-resolution imagery. This imagery is instrumental in observing cloud formations over Lake Michigan. These details are essential for understanding and predicting weather patterns to lake effect precipitation.

### Weather Station Data

#### Source:
This data is sourced from ground-based weather stations strategically located near the lakeshore of Lake Michigan. These stations are ideally placed to capture detailed local atmospheric conditions that satellite imagery might miss.

#### Content:
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

# 4. Hybrid Model Architecture

The hybrid CNN-RNN model effectively combines Cloud Imagery data and Meteorological data. The model architecture is detailed below:

## CNN for Cloud Imagery
- **Input**: Processes sequences of cloud images, each sequence shaped as (9, 64, 64, 1) which is of 9 hrs of daytime images.
- **Layers**:
  - Conv3D layers extract spatial-temporal features.
  - BatchNormalization and MaxPooling3D layers enhance and reduce feature dimensions.
  - A Flatten layer followed by a Dense layer finalizes the CNN feature extraction.

## RNN for Meteorological Data
- **Input**: Handles time-series meteorological data shaped as (7, 7) which is 7 days of sequence.
- **Layers**:
  - Multiple LSTM layers learn temporal patterns with increasing depth and complexity.
  - Each LSTM layer is accompanied by BatchNormalization and Dropout to improve learning and reduce overfitting.
  - The final LSTM output is processed through a Dense layer.

## Integration and Output
- **Concatenation**: Features from CNN and RNN are combined to leverage both Cloud Imagery data and Meteorological data.
- **Final Layers**: A Dense layer processes the concatenated features, leading to a softmax output layer that classifies weather conditions.

## Model Compilation
- Uses Adam optimizer and categorical crossentropy loss, focusing on multi-class classification accuracy.

This architecture enables the model to robustly predict weather conditions by analyzing both the visual and temporal data, making it highly effective for comprehensive weather analysis.

## Conclusion

The hybrid CNN-RNN model capitalizes on the unique strengths of both Convolutional Neural Networks and Recurrent Neural Networks to process and interpret complex spatial and temporal data. By integrating cloud imagery and meteorological data, the model offers a robust framework for accurate and reliable weather forecasting. The combination of CNNs for extracting detailed spatial features from cloud sequences and RNNs for capturing dynamic temporal patterns in meteorological data ensures comprehensive analysis capabilities. This dual approach enhances the model's predictive accuracy and makes it a powerful tool for advanced weather prediction tasks.


