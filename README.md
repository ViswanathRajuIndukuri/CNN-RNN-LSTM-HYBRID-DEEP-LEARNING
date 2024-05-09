# Lake Effect Precipitation Prediction

# CNN & RNN-LSTM HYBRID DEEP LEARNING MODEL

# Introduction
This project focuses on predicting lake effect precipitation using Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs). It involves the use of meteorological variables and satellite cloud imagery.

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
