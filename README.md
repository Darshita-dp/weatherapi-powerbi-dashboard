# WeatherAPI Power BI Dashboard

![Dashboard Preview](screenshots/main-dashboard.png)

## Overview
This project is an interactive Power BI dashboard that analyzes real-time weather data using the WeatherAPI service. The dashboard consolidates current weather conditions, weekly forecast trends, and air quality indicators into a single visual interface designed for quick decision-making and environmental awareness.

The goal of this project was to demonstrate how API-based data can be transformed, modeled, and visualized using Power BI to create an informative analytics dashboard.

---

## Key Features

### Current Weather Overview
Displays real-time weather metrics for the selected city, including:
- Temperature
- Weather condition
- Humidity
- Wind speed
- Pressure
- Visibility
- UV index
- Precipitation

### 7-Day Forecast Analysis
A visual representation of temperature trends across the next 7 days, allowing users to quickly identify weather patterns.

### Air Quality Index (AQI) Monitoring
The dashboard evaluates air quality using pollutant indicators such as:

- PM2.5
- PM10
- NO2
- O3
- SO2
- CO

Each pollutant is categorized using AQI health standards and displayed with:
- status labels
- color indicators
- health suggestions

### Rain Probability Visualization
Shows the likelihood of rainfall across forecast days, helping users understand precipitation patterns.

---

## Data Source

Weather data is retrieved from:

WeatherAPI  
https://www.weatherapi.com/

The API returns JSON data which is imported into Power BI using the **Web connector**.

---

## Data Processing Workflow

The data pipeline for this project follows the structure below:

WeatherAPI → Power Query → Data Model → DAX Measures → Power BI Dashboard

Key steps include:
1. Connecting to the WeatherAPI endpoint
2. Expanding nested JSON structures
3. Cleaning and transforming data using Power Query
4. Creating analytical measures using DAX
5. Building an interactive dashboard with visual insights

---

## Technical Skills Demonstrated

- API Data Integration
- Power BI Dashboard Design
- Power Query Data Transformation
- DAX Measures & Conditional Logic
- Data Modeling
- Data Visualization

---

## Project Structure
weatherapi-powerbi-dashboard
│
├── README.md
├── .gitignore
├── dashboard/
│ └── WeatherAPI_Dashboard.pbix
├── screenshots/
│ ├── main-dashboard.png
│ ├── forecast-section.png
│ └── aqi-section.png
├── dax/
│ └── dax-measures.md
└── data/
└── sample-data-or-note.md


---

## Key Learning Outcomes

Through this project I practiced:

- integrating external API data into Power BI
- transforming nested JSON data structures
- building reusable DAX measures
- implementing AQI classification logic
- designing a user-friendly analytics dashboard

---

## Author

Darshita Patel  
Master’s in Information Systems  
Illinois State University