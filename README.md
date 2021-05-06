# pv_forecast
Here, a forecast for the energy production of a photovoltaic system is 
created.   
Therefore, the data is transferred from the Fronius Solar API of the inverter 
to a PostgreSQL database on a Raspberry Pi.  
Before that I also look on the data provided by the Fronius Solarweb reports 
and data generated by the USB port from the inverter.   
Hardware which was used is a Fronius Primo 5.0-1 inverter, and the Raspberry Pi 
2 Model B.

## data
- pv.csv: Data with 30 minutes resolution from Fronius Primo 5.0-1 inverter USB 
  port.
- pv_day.csv: Daily data from fronius solarweb reports.

## pi
- fronius_to_db.py: Gets data from inverter and saves it in a PostgreSQL 
  database on the Raspberry Pi.
- sun_to_cron: Creates a crontab to run the fronius_to_db.py only while the sun 
  is shining.

## scripts
### jupyter  
- 30min_initial.ipynb: Initial analysis and an explanation for the columns of 
  USB data.
- 30min_further.ipynb: Further analysis of USB data.
- daily.ipynb: First look on daily data from Fronius Solarweb.
- fronius_solar_api.ipynb: Exploration of Fronius Solar API.
- owm_api.ipynb: Exploration of OWM API.
- results.ipynb: Creates error measures and plots to compare predictions.
- sun_rise_set.ipynb: Exploration of sunrise-sunset.org API.

### sql
- pv.sql creates a view without text columns and missing data.
- pv_org.sql creates a database and uploads the USB data.
- ws.sql creates a time series with 30 minutes frequency based on the energy 
  ('energy_positiv_ws').
- results.sql creates a table for saving forecasts. The table is initialized 
  with forecast based on different means.
