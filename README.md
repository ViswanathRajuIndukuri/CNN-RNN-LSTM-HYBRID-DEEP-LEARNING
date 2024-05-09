# Lake Effect Precipitation Prediction

# CNN & RNN-LSTM HYBRID DEEP LEARNING MODEL

# Introduction
In this project, I explore a hybrid deep learning model combining Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) to predict lake effect precipitation One, Two, and Three days in advance. This advanced model architecture leverages both image and sequential data to enhance predictive performance.

# Data Preprocessing
### 1. Data Preprocessing and Exploratory Data Analysis (EDA)
- **Data Cleaning**: Features are renamed for clarity, date and time columns combined into a single column focused on UTC time, and missing or non-numerical values are handled efficiently.
- **Feature Engineering**: Removed features with a high percentage of missing values and highly correlated features to reduce redundancy and improve model accuracy.
- **Temporal Data Handling**: Data is sorted chronologically.
- **Data imputation**: Implemented data imputation strategies and data type conversions to prepare the dataset for modeling.

### 2. Image Analysis
- **Satellite Image Processing**: Analyzed and processed satellite images, removing those with poor lighting or distortion, focusing on clear images available between 14:00 and 22:00 UTC.
- **Data Filtration**: Filterd image data based on sunlight availability and image clarity to enhance data quality for CNN modeling.

### 3. Data Saving and Organization
- **File Management**: Data is organized into different files tailored for specific parts of the analysis:
  - `les_data.csv` - Contains all processed features.
  - `meteorological_data.csv` - Dedicated to meteorological features for RNN processing.
  - `filtered_les_cld_imgs.csv` - Includes DateTime_UTC and lake_data_2D columns for CNN processing.

# Visualizations
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
