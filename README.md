# wildfire_data

Data sources:
1. https://www.kaggle.com/rtatman/188-million-us-wildfires
2. https://stackoverflow.com/questions/3200984/where-can-i-find-historical-raw-weather-data (stackoverflow answer for getting historical weather data -- we may need to scrape weather sites... or trim data to only recent time frame)
3. https://www.kaggle.com/sobhanmoosavi/us-weather-events?select=US_WeatherEvents_2016-2019.csv
Weather events 

#### Notebook summary:
generate_data_with_target: resources to generate
(1) a 20k row data sample from the large kaggle sqlite dataset
(2) a 892007-row dataset from the large kaggle sqlite dataset which requires the following features to be present:
	DISCOVERY_TIME, CONT_TIME, DISCOVERY_DATE, and CONT_DATE

calc_cont_time: calculates our target variable of delta in containment time from the four features listed above (DISCOVERY_TIME, CONT_TIME, DISCOVERY_DATE, and CONT_DATE)



