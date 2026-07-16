# Global Weather Trend Forecasting

A comprehensive data science project analyzing global weather patterns, forecasting temperature trends, detecting anomalies, and exploring environmental and geographical relationships using machine learning and time-series analysis.

## Project Overview

This project uses the Global Weather Repository dataset to perform end-to-end weather data analysis, including data preprocessing, exploratory data analysis, temperature forecasting, anomaly detection, model comparison, ensemble learning, climate analysis, air-quality analysis, feature importance, and geographical pattern exploration.

The project was developed as part of a Machine Learning technical assessment.

## Dataset

The project uses the **Global Weather Repository** dataset available on Kaggle.

The dataset contains historical weather observations from locations across the world, including:

- Temperature
- Humidity
- Atmospheric pressure
- Wind speed and direction
- Precipitation
- Cloud cover
- Visibility
- UV index
- Air-quality measurements
- Geographical coordinates
- Astronomical information

## Project Workflow

### 1. Data Cleaning and Preprocessing

The dataset was inspected and prepared before analysis.

The preprocessing steps included:

- Checking for missing values
- Checking duplicate records
- Converting `last_updated` into datetime format
- Removing redundant features represented in alternative measurement units
- Examining potential outliers using the Interquartile Range (IQR) method
- Applying feature scaling where required

Extreme weather observations were not automatically removed because unusual values may represent genuine weather events rather than data errors.

### 2. Exploratory Data Analysis

Exploratory Data Analysis was performed to identify patterns and relationships between weather parameters.

The analysis included:

- Correlation analysis between major weather variables
- Temperature distribution analysis
- Precipitation distribution analysis
- Temperature and humidity relationship
- Humidity and cloud-cover relationship
- Temperature and precipitation visualizations

### 3. Time-Series Forecasting

The `last_updated` feature was used as the temporal component for time-series analysis.

New Delhi was selected as a representative location to maintain a consistent chronological weather sequence instead of combining unrelated observations from different geographical locations.

Daily temperature observations were prepared chronologically and divided into training and testing periods while preserving their temporal order.

Seasonal features were created using cyclical transformations of the day of the year.

### 4. Machine Learning Models

Multiple regression models were trained and evaluated for temperature forecasting:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- K-Nearest Neighbors Regressor
- Support Vector Regressor

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

Among the individual models, Random Forest achieved the best overall performance.

### 5. Ensemble Forecasting

An ensemble was created by combining predictions from the two strongest individual models:

- Random Forest Regressor
- K-Nearest Neighbors Regressor

The predictions were averaged to generate the final ensemble forecast.

The ensemble improved the forecasting performance compared with the individual models.

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| RF + KNN Ensemble | 2.519 | 3.329 | 0.077 |
| Random Forest Regressor | 2.848 | 3.516 | -0.030 |
| KNN Regressor | 2.843 | 3.625 | -0.095 |
| Decision Tree Regressor | 3.444 | 4.188 | -0.462 |
| Linear Regression | 3.622 | 4.487 | -0.677 |
| Support Vector Regressor | 5.136 | 5.866 | -1.866 |

### 6. Anomaly Detection

Isolation Forest was used to detect unusual combinations of weather conditions.

The anomaly detection process considered variables including:

- Temperature
- Humidity
- Atmospheric pressure
- Wind speed
- Precipitation

Detected anomalies were analyzed separately instead of automatically removing them, as extreme observations may represent genuine weather events.

### 7. Climate Analysis

Monthly average temperature trends were compared across representative cities:

- New Delhi
- London
- Tokyo
- Cairo

The analysis demonstrated clear seasonal variations and differences in regional temperature patterns.

Because the dataset covers approximately two years, the results represent multi-year seasonal patterns rather than long-term climate-change conclusions.

### 8. Environmental Impact Analysis

Relationships between weather conditions and major air-quality pollutants were analyzed.

The pollutants included:

- Carbon Monoxide
- Ozone
- Nitrogen Dioxide
- Sulphur Dioxide
- PM2.5
- PM10

Correlation analysis was used to identify relationships between pollution levels and temperature, humidity, pressure, wind speed, and precipitation.

### 9. Feature Importance

A Random Forest model was used to analyze the relative importance of weather parameters for temperature prediction.

The analysis identified UV index, atmospheric pressure, and humidity as the most influential features among the selected variables.

### 10. Spatial and Geographical Analysis

Latitude and longitude were used to visualize the global spatial distribution of temperature observations.

Country-level aggregation was also performed to compare average weather conditions and identify geographical variations across different parts of the world.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Project Structure

```text
weather-trend-forecasting/
│
├── notebooks/
│   └── weather_analysis.ipynb
│
├── data/
│   └── GlobalWeatherRepository.csv
│
├── README.md
├── requirements.txt
└── .gitignore


## How to Run

Clone the repository and navigate to the project directory.

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the following notebook:

```text
notebooks/weather_analysis.ipynb
```

Run the notebook cells sequentially to reproduce the complete analysis.

## Key Findings

- Weather variables exhibit meaningful relationships, particularly between temperature, humidity, cloud cover, and UV index.
- Precipitation is strongly right-skewed, with most observations recording little or no rainfall.
- Random Forest performed best among the individual forecasting models.
- The Random Forest and KNN ensemble achieved the best overall forecasting performance with an MAE of 2.519 and RMSE of 3.329.
- Isolation Forest successfully identified unusual combinations of weather conditions.
- Regional temperature trends showed clear seasonal and geographical variations.
- Humidity showed notable correlations with several air-quality pollutants.
- UV index, atmospheric pressure, and humidity were the most important selected features for temperature prediction.

## Conclusion

This project demonstrates an end-to-end data science workflow for global weather analysis, including data preprocessing, exploratory data analysis, time-series forecasting, machine learning model comparison, ensemble learning, anomaly detection, environmental analysis, and geographical exploration.

The results demonstrate the challenges of weather forecasting using limited historical data while showing that combining predictions from multiple models can improve overall forecasting performance.