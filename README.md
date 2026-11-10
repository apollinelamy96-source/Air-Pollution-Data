# Analysis of air pollution near restaurants with duct violations in New York City — 06/2026 to 09/2026

This repository contains data, analytic code, and findings that support portions of the article, "[TKTKTKTK](https://www.google.com/)," published Month Date, Year. 
I did not publish the article yet. 

## Data

This analysis uses two datasets. They come from the following sources:

* NYC Department of Health and Mental Hygiene (via NYC Open Data):
   * `data/DOHMH_New_York_City_Restaurant_Inspection_Results.csv`: Restaurant inspection results, including violations.
* PurpleAir (community air quality sensors):
   * `output/sensor_data/`: Hourly PM2.5 readings for each of the 10 sensors, downloaded through the PurpleAir API.

The inspection file contains, among others, the following columns relevant to the analysis:

* `ZIPCODE` — ZIP code of the restaurant
* `VIOLATION DESCRIPTION` — duct violation

The sensor files contain:

* `pm2.5_atm` — PM2.5 concentration in µg/m³, hourly average
* `sensor_index` — PurpleAir sensor ID
* `zone` — "restaurant" (ZIP codes with the most duct violations) or "no restaurant" (ZIP codes with the fewest)

## Methodology

The notebook `notebooks/restaurants_duct.ipynb` does this analysis:

Part 1: Duct violations by ZIP code

* Filters the inspection data to duct violations and ranks ZIP codes. The 5 ZIP codes with the highest and the 5 with the lowest concentration of duct violations were selected.

The notebook `notebooks/requests_purple_air.ipynb` performs the following analysis:

Part 2: Downloading sensor data

* Downloads hourly PM2.5 data from June 1 to September 30, 2026 for 10 sensors (one per selected ZIP code), saves one file per sensor, and combines them with a `zone` column.

The notebook `notebooks/analysis.ipynb` performs the following analysis:

Part 3: Comparison

* Compares the mean and median PM2.5 in both zones, with and without three sensors set aside (285560 and 150174 for extreme spikes, 319136 for having only 1,207 hourly readings instead of about 2,900).

## Outputs

The notebooks output this spreadsheet, which contains hourly PM2.5 readings for all 10 sensors with their zone: `output/air_pollution.csv`. The individual sensor files are in `output/sensor_data/`.

## Running the analysis yourself

You can run the analysis yourself. To do so, you'll need the following installed on your computer:

* Python 3
* The Python libraries specified in `requirements.txt`

You will also need a free PurpleAir API key, which you paste into `requests_purple_air.ipynb`.

## Licensing

All code in this repository is available under the [MIT License](https://opensource.org/licenses/MIT). The data file in the output/ directory is available under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0) license. All files in the data/ directory are released into the public domain.

## Feedback / Questions?

Contact YOUR NAME HERE at [your.name@email.com](mailto:your.name@email.com).
