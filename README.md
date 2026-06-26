# Holiday Planner Project

A Streamlit holiday recommendation app that compares destinations using weather, nightlife, nearby amenities, flight prices and accommodation costs.

The repository contains both the data retrieval notebook and the Streamlit app. The notebook generates processed CSV files, and the app reads those files from the `data/` folder to power the interactive dashboard.

## Features

- Compare holiday destinations by weather, cost, nightlife and amenities
- View daily weather forecast charts by destination
- Compare flight prices, accommodation costs and estimated total trip cost
- Adjust recommendation priorities using Streamlit sliders
- Explore restaurants, bars, nightclubs, attractions and places to stay on an interactive map

## Repository structure

```text
holiday_planner_project/
├── app.py
├── holiday_planner_data_retrieval.ipynb
├── requirements.txt
├── README.md
├── .env.example.txt
├── .gitignore
├── .streamlit/
│   └── config.toml
├── data/
│   ├── destination_recommendations.csv
│   ├── places.csv
│   ├── selected_travel_options.csv
│   └── weather.csv
├── pages/
│   ├── 1_Weather.py
│   ├── 2_Flights_and_Cost.py
│   ├── 3_Recommendation.py
│   └── 4_Map_and_Places.py
├── src/
│   ├── __init__.py
│   ├── data_loader.py
│   └── ui.py
└── tests/
    └── test_data_loader.py
```

## Data sources

The data pipeline uses:

- Google Geocoding API for coordinates and country information
- Google Places API for nearby restaurants, bars, nightclubs, lodging and attractions
- OpenWeather API for weather forecast data
- SerpApi for structured Google Flights and Google Hotels results

API keys should be stored locally in a `.env` file and should not be committed to GitHub. The repository includes `.env.example.txt` as a template.

## Data files

The Streamlit app is CSV-driven and uses these files from the `data/` folder:

| File | Purpose |
|---|---|
| `destination_recommendations.csv` | Main destination table with scores, costs and recommendation fields |
| `weather.csv` | Daily weather forecast rows for each destination |
| `places.csv` | Nearby places used by the map and places page |
| `selected_travel_options.csv` | Selected flight and accommodation option for each destination |

## Setup

Clone the repository:

```bash
git clone https://github.com/FBackhouse1/holiday_planner_project.git
cd holiday_planner_project
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Create a local `.env` file using `.env.example.txt` as a guide:

```text
GOOGLE_MAPS_API_KEY=your_google_maps_api_key_here
OPENWEATHER_API_KEY=your_openweather_api_key_here
SERPAPI_API_KEY=your_serpapi_api_key_here
```

## Running the data pipeline

Open and run:

```text
holiday_planner_data_retrieval.ipynb
```

The notebook collects API data, processes it and outputs CSV files for the app.

## Running the app

From the repository root, run:

```bash
streamlit run app.py
```

The app will open in your browser.

## Notes

- The app reads processed CSV files from `data/`.
- Weather data uses the available OpenWeather forecast window.
- Flight and accommodation costs use the travel dates set in the notebook.
- `.gitignore` is included to avoid committing local secrets, raw data, cache files and virtual environments.
