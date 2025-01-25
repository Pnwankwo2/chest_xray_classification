# Milking the Data
![alt text](Resources/banner_image.jpg)

## Milk Production Prediction 
The Project Goal is to build an Artificial Neural Network (ANN) to accurately predict the average milk yield of cows based on environmental conditions (temperature, humidity, cold stress, precipitation) and lactation cycle information (lactation number, calving date, first record date). 

1. Dataset

The dataset has been extracted from the milk record database of the Braunvieh-CH breeding organisation, from https://zenodo.org/records/3962046. (Duruz, S., & Flury, C. (2020). The Rights of the dataset is cc0-1.0 icon Creative Commons Zero v1.0 Universal making it freely usable without restriction.

The provided dataset contains information on: 

cow and lactation cycle: lactation number, date of calving, date of first record of calv in the alp, average quantity of milk (measured in kilograms).

Environmental conditions: Temperature Humidity Index (THI) averaged over 3 and 30 days, Cold Stress Index (CSI) averaged over 3 and 30 days, precipitation during Spring.

The DataFrame has 20,000 rows and 10 columns for a period ranginwg from years 2000 to 2015 

The average quantity of milk is the defined target column.

![Histogram of Average Milk Yield](histogram.png)





2. Data Preprocessing:

Data Cleaning:
Handle missing values and outliers.
Encode categorical features if necessary.
Feature Engineering.
Normalize or standardize numerical features.
Prepare the data for training and testing.



Addendum No.1: References/Citations
Duruz, S., & Flury, C. (2020). Milk production and environmental conditions of mountain-pastured Braunvieh cows between 2000 and 2015 [Data set]. Zenodo. https://doi.org/10.5061/dryad.z612jm68g


