# wildfire_data

This project aimed to analyze the time delta between discovery and containment
time to predict the fire class size. In initial attempts to classify fire severity based on our Hours to
Containment target, a Linear Regression model indicated that we didn’t have sufficient feature
data to predict on said target. Across 5 folds with a testing size of 33%, the training R 2
 measured
at a mean of 0.101 +/= .008 and testing R 2
 at .102 +/= .001.
We then used a Decision Tree to model the data as it’d allow for the reasoning for the predictions
to be deduced, and could thus help in identifying why a potential wildfire might be severe. The
Decision Tree was trained on the features and labels, using 5-fold cross-validation and a testing
size of 33%. The training and testing accuracy increased fairly tightly in step from depths 1-8, at
which point the model started to overfit, resulting in a clear diversion at depth 16. The Decision
Tree model produced a maximum testing accuracy at depth 14 of around .646 +/= .0005. We also
found out via Gini criterion that our engineered feature, hours to containment, had a high feature
importance.
Next using the Decision Tree model as a basis, we trained a Random Forest on the Fire Size
Category target. We produced a maximum testing accuracy for the Random Forest of 0.67 +/-
.0008, with a corresponding training accuracy of .70 +/- .0003, our highest accuracy thus far.
The features we found most important in our model were longitude, latitude, and hours to
containment. As mentioned earlier, longitude and latitude are likely significant as they relate to
the climate and have the potential to serve as a representation of the type of weather common to
a certain location. Hours to Containment is also a fairly robust predictor for fire size as it’s
positively correlated with Fire Size Class given that a larger Hours to Containment value
typically means the fire has had time to cover more ground. 



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



