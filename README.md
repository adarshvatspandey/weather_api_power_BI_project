# weather_api_power_BI_project_dashboard

## 📖 Overview

The Weather Analytics Dashboard is an interactive Business Intelligence solution developed in Power BI using real-time Weather API data. The dashboard provides comprehensive weather insights, air quality monitoring, and forecasting information through dynamic visualizations and user-friendly analytics.

This project demonstrates the use of API integration, data transformation, data modeling, DAX calculations, and advanced dashboard design techniques to create a centralized weather monitoring platform.

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

## 💡 Skills Demonstrated

* API Integration
* Data Cleaning & Transformation
* Power Query Development
* DAX Calculations
* Data Modeling
* Dashboard Design
* Business Intelligence
* Data Visualization
* Analytical Reporting
  📊 WEATHER API PROJECT – KPIs

1. Current Temperature
2. Air Quality Suggestion
3. Carbon Monoxide (CO) Status
4. Nitrogen Dioxide (NO₂) Status
5. Last Updated Timestamp
6. PM10 Pollution Gauge
7. Average Temperature
8. Maximum Temperature
9. Minimum Temperature
10. Average Humidity
11. Maximum Wind Speed
12. Average Visibility
13. Total Locations Monitored

====================================================

🧮 DAX MEASURES

1️⃣ City Temperature

City Temp =
FORMAT(
    SELECTEDVALUE('Current Data'[current.temp_c]),
    "0.0"
) & " °C"

----------------------------------------------------

2️⃣ AQI Suggestion

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

----------------------------------------------------

3️⃣ CO Color Indicator

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

----------------------------------------------------

4️⃣ NO₂ Color Indicator

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

----------------------------------------------------

5️⃣ Last Updated KPI

Last_Updates_Current =
"Last Updated: " &
FORMAT(
    MAX('Current Data'[current.last_updated]),
    "dd mmm"
)

----------------------------------------------------

6️⃣ PM10 Gauge Value

MaxValue = 70

left_value_PM10 =
[MaxValue] -
SUM('Current Data'[current.air_quality.pm10])

----------------------------------------------------

7️⃣ Average Temperature

Avg Temperature =
AVERAGE('Current Data'[current.temp_c])

----------------------------------------------------

8️⃣ Maximum Temperature

Max Temperature =
MAX('Current Data'[current.temp_c])

----------------------------------------------------

9️⃣ Minimum Temperature

Min Temperature =
MIN('Current Data'[current.temp_c])

----------------------------------------------------

🔟 Average Humidity

Avg Humidity =
AVERAGE('Current Data'[current.humidity])

----------------------------------------------------

1️⃣1️⃣ Maximum Wind Speed

Max Wind Speed =
MAX('Current Data'[current.wind_kph])

----------------------------------------------------

1️⃣2️⃣ Average Visibility

Avg Visibility =
AVERAGE('Current Data'[current.vis_km])

----------------------------------------------------

1️⃣3️⃣ Total Locations

Total Locations =
DISTINCTCOUNT('Current Data'[location.name])

====================================================

🎯 PROJECT OUTCOMES

• Built a real-time Weather Analytics Dashboard using Weather API and Power BI.

• Created 13 KPI metrics and DAX measures for monitoring temperature, humidity, wind speed, visibility, and air quality.

• Implemented dynamic AQI-based health recommendations and pollution indicators using conditional formatting.

• Enabled real-time weather tracking and environmental monitoring through interactive dashboards and KPI cards.

• Delivered actionable insights on weather conditions and air quality to support informed decision-making.

