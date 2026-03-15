
# DAX Measures

This file documents the main DAX measures used in the WeatherAPI Power BI Dashboard.
These measures support KPI cards, AQI indicators, color logic, health suggestions,
forecast labels, and formatting across the report.

---

## 1. Weather Display Measures

### Date_Updated
Purpose: Displays the latest refresh date from the current weather data.

Date_Updated =
"Last Updated, "
& FORMAT(
    FIRSTNONBLANK('Current'[current.last_updated],""),
    "dd MMM"
)

### Temp_Display
Purpose: Displays current temperature in Celsius.

Temp_Display =
MAX('Current'[current.temp_c]) & " °C"

### Condition_Text
Purpose: Displays the current weather condition text.

Condition_Text =
FIRSTNONBLANK('Current'[current.condition.text],"")

### Humidity

Humidity =
MAX('Current'[current.humidity]) & " %"

### Wind_Speed

Wind_Speed =
MAX('Current'[current.wind_kph]) & " kph"

### Visibility

Visibility =
MAX('Current'[current.vis_km])

### Pressure

Pressure =
MAX('Current'[current.pressure_in])

### UV_Index

UV_Index =
MAX('Current'[current.uv])

### Precipitation

Precipitation =
MAX('Current'[current.precip_mm]) & " mm"

---

## 2. Forecast Measures

### Forecast_Day_1

Forecast_Day_1 =
MAX('Forecast'[forecastday.day.avgtemp_c]) & " °C"

### Rain_Chance_Day_1

Rain_Chance_Day_1 =
MAX('Forecast'[forecastday.day.daily_chance_of_rain]) & "%"

---

## 3. AQI Status Measures

### AQI_Status_PM25

AQI_Status_PM25 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm2_5]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Good",
    AQI <= 100, "Moderate",
    AQI <= 150, "Unhealthy for Sensitive",
    AQI <= 200, "Unhealthy",
    AQI <= 300, "Very Unhealthy",
    "Hazardous"
)

### AQI_Status_PM10

AQI_Status_PM10 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm10]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Good",
    AQI <= 100, "Moderate",
    AQI <= 150, "Unhealthy for Sensitive",
    AQI <= 200, "Unhealthy",
    AQI <= 300, "Very Unhealthy",
    "Hazardous"
)

---

## 4. AQI Color Measures

### AQI_Color_PM25

AQI_Color_PM25 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm2_5]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d645",
    AQI <= 100, "#f6c570",
    AQI <= 150, "#ef8d3d",
    AQI <= 200, "#ed5b53",
    AQI <= 300, "#8c5cd7",
    "#7e0023"
)

### AQI_Color_PM10

AQI_Color_PM10 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm10]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "#43d645",
    AQI <= 100, "#f6c570",
    AQI <= 150, "#ef8d3d",
    AQI <= 200, "#ed5b53",
    AQI <= 300, "#8c5cd7",
    "#7e0023"
)

---

## 5. AQI Suggestion Measures

### AQI_Suggestion_PM25

AQI_Suggestion_PM25 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm2_5]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality for most people",
    AQI <= 150, "Sensitive groups should reduce outdoor time",
    AQI <= 200, "Limit prolonged outdoor exertion",
    AQI <= 300, "Avoid outdoor activity if possible",
    "Stay indoors and wear a mask if outside"
)

### AQI_Suggestion_PM10

AQI_Suggestion_PM10 =
VAR AQI =
ROUND(
    SELECTEDVALUE('Current'[current.air_quality.pm10]),
    1
)
RETURN
SWITCH(
    TRUE(),
    AQI <= 50, "Air is clean and healthy",
    AQI <= 100, "Acceptable air quality for most people",
    AQI <= 150, "Sensitive groups should reduce outdoor time",
    AQI <= 200, "Limit prolonged outdoor exertion",
    AQI <= 300, "Avoid outdoor activity if possible",
    "Stay indoors and wear a mask if outside"
)

---

## Notes

- Weather data is sourced dynamically from WeatherAPI.
- Data is imported using Power BI Web connector.
- Power Query is used to transform nested JSON responses.
- DAX measures support KPI visuals, AQI indicators, labels, and conditional formatting.
