# weather_API_Power_BI_Project_Dashboard

## 📖 Overview

The Weather Analytics Dashboard is an interactive Business Intelligence solution developed in Power BI using real-time Weather API data. The dashboard provides comprehensive weather insights, air quality monitoring, and forecasting information through dynamic visualizations and user-friendly analytics.

This project demonstrates the use of API integration, data transformation, data modeling, DAX calculations, and advanced dashboard design techniques to create a centralized weather monitoring platform.
 ![image](https://github.com/adarshvatspandey/weather_api_power_BI_project/blob/3787c81fe50ef933363fbe4ed53823ee2d765bf2/weather.jpg) 
 
---

## 🎯 Project Objectives

* Monitor real-time weather conditions.
* Analyze air quality metrics across locations.
* Track environmental indicators such as humidity, visibility, pressure, and wind speed.
* Visualize weather forecast trends.
* Provide rainfall probability insights.
* Enable city-wise weather comparison.

---
 📊 Dashboard Preview

 ![image](https://github.com/adarshvatspandey/weather_api_power_BI_project/blob/5c0054d7bc4ecfbe9cb175d5939c3625e6849871/Dashboard.png)

## 📊 Dashboard Features

### 🌡️ Current Weather Monitoring

* Current Temperature (°C)
* Weather Condition Status
* Last Updated Information
* Multi-City Weather Comparison

### 📅 Forecast Analysis

* Multi-Day Temperature Forecast
* Weather Trend Visualization
* Daily Forecast Tracking

### 🌫️ Air Quality Analysis

* Air Quality Index (AQI)
* PM10 Monitoring
* PM2.5 Monitoring
* Carbon Monoxide (CO)
* Nitrogen Dioxide (NO₂)
* Sulfur Dioxide (SO₂)

### 🌍 Environmental Metrics

* Humidity
* Wind Speed
* Atmospheric Pressure
* Visibility
* UV Index
* Precipitation

### 🌅 Astronomical Information

* Sunrise Time
* Sunset Time

### ☔ Rainfall Prediction

* Daily Chance of Rain Analysis
* Rain Probability Comparison

---

## 🛠️ Technologies Used

* Power BI Desktop
* Weather API
* Power Query
* DAX (Data Analysis Expressions)
* Data Modeling
* Data Visualization
* Business Intelligence Reporting

---

## 📂 Dataset Information

The dashboard utilizes Weather API data containing:

* Current Weather Data
* Forecast Data
* Air Quality Data
* Location Information
* Sunrise & Sunset Information
* Environmental Indicators

---

## 📈 Key Insights

* Real-time weather monitoring across cities.
* Air quality assessment and pollution tracking.
* Temperature forecasting and trend analysis.
* Rainfall probability prediction.
* Environmental condition monitoring.
* Interactive weather comparison dashboard.

---

# 📊 KPI Metrics & DAX Measures

## 🎯 Key Performance Indicators (KPIs)

The dashboard tracks the following KPIs to monitor weather conditions and air quality in real time:

* 🌡️ Current Temperature
* 💨 Air Quality Suggestion
* 🏭 Carbon Monoxide (CO) Status
* 🌫️ Nitrogen Dioxide (NO₂) Status
* 🕒 Last Updated Timestamp
* 📈 PM10 Pollution Gauge
* 🌡️ Average Temperature
* 🔥 Maximum Temperature
* ❄️ Minimum Temperature
* 💧 Average Humidity
* 🌪️ Maximum Wind Speed
* 👀 Average Visibility
* 📍 Total Locations Monitored

---

# 🧮 DAX Measures

## Current Temperature

```DAX
City Temp =
FORMAT(
    SELECTEDVALUE('Current Data'[current.temp_c]),
    "0.0"
) & " °C"
```

## Air Quality Recommendation

```DAX
AQI Suggestion =
VAR AQI = MAX('Current Data'[current.air_quality.pm10])

RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality, stay active",
    AQI <= 150, "Sensitive groups should reduce outdoor time",
    AQI <= 200, "Limit prolonged outdoor exertion",
    AQI <= 300, "Avoid outdoor activity if possible",
    "Stay indoors, wear mask if outside"
)
```

## Carbon Monoxide Indicator

```DAX
CO Color =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current Data'[current.air_quality.CO]),
    0
)

RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946",
    AQI <= 100, "#ffd570",
    AQI <= 150, "#ff9800",
    AQI <= 200, "#d99343",
    AQI <= 300, "#ff5b0f",
    "#d95243"
)
```

## Nitrogen Dioxide Indicator

```DAX
NO2Color =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current Data'[current.air_quality.No2]),
    0
)

RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d946",
    AQI <= 100, "#ffd570",
    AQI <= 150, "#ff9800",
    AQI <= 200, "#d99343",
    AQI <= 300, "#ff5b0f",
    "#d95243"
)
```

## Last Updated Timestamp

```DAX
Last_Updates_Current =
"Last Updated: " &
FORMAT(
    MAX('Current Data'[current.last_updated]),
    "dd mmm"
)
```

## PM10 Gauge Calculation

```DAX
MaxValue = 70
```

```DAX
left_value_PM10 =
[MaxValue] -
SUM('Current Data'[current.air_quality.pm10])
```

## Average Temperature

```DAX
Avg Temperature =
AVERAGE('Current Data'[current.temp_c])
```

## Maximum Temperature

```DAX
Max Temperature =
MAX('Current Data'[current.temp_c])
```

## Minimum Temperature

```DAX
Min Temperature =
MIN('Current Data'[current.temp_c])
```

## Average Humidity

```DAX
Avg Humidity =
AVERAGE('Current Data'[current.humidity])
```

## Maximum Wind Speed

```DAX
Max Wind Speed =
MAX('Current Data'[current.wind_kph])
```

## Average Visibility

```DAX
Avg Visibility =
AVERAGE('Current Data'[current.vis_km])
```

## Total Locations Monitored

```DAX
Total Locations =
DISTINCTCOUNT('Current Data'[location.name])
```

---

# 🚀 Project Outcomes

* Built a real-time Weather Analytics Dashboard using Power BI and Weather API data.
* Developed KPI-driven insights for temperature, humidity, visibility, wind speed, and air quality monitoring.
* Implemented dynamic AQI recommendations and conditional formatting using DAX.
* Enabled real-time environmental monitoring through interactive dashboards and visual indicators.
* Improved data accessibility by transforming raw API responses into actionable business insights.
