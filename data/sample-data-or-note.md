# Data Source Information

## Weather Data Source
The data used in this Power BI dashboard is retrieved from the WeatherAPI service.

API documentation:
https://www.weatherapi.com/docs/

The API provides real-time and forecast weather information in JSON format.

## Example API Request

Current weather endpoint:

https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=Chicago

Example parameters:
- q → city name
- key → API authentication key

## Data Fields Used

The dashboard extracts and transforms the following fields:

Weather Metrics
- temperature
- humidity
- wind speed
- pressure
- visibility
- precipitation

Air Quality Indicators
- PM2.5
- PM10
- NO2
- O3
- CO
- SO2

Forecast Data
- daily temperature
- rain probability
- sunrise / sunset

## Data Transformation

The JSON API response is imported into Power BI using **Power Query (Web connector)** and expanded into structured tables.

Steps include:
1. Connecting to the API endpoint
2. Expanding nested JSON fields
3. Renaming columns
4. Creating calculated measures using DAX

## Notes

- The dataset is generated dynamically via API calls.
- No static dataset is stored in this repository.
- To reproduce the dashboard, users must generate their own API key from WeatherAPI.

https://www.weatherapi.com/