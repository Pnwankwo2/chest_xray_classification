# Milking the Data
![alt text](Resources/banner_image.jpg)

## Milk Production Prediction 
The Project Goal is to build an Artificial Neural Network (ANN) to accurately predict the average milk yield of cows based on environmental conditions (temperature, humidity, cold stress, precipitation) and lactation cycle information (lactation number, calving date, first record date). 

1. Dataset

The dataset has been extracted from the milk record database of the Braunvieh-CH breeding organisation, from https://zenodo.org/records/3962046. (Duruz, S., & Flury, C. (2020). The Rights of the dataset is cc0-1.0 icon Creative Commons Zero v1.0 Universal, making it freely usable without restriction.

The dataset encompasses 20,000 cows and includes 10 variables, therefore represented as a DataFrame with 20,000 rows and 10 columns. The data spans a period from years 2000 to 2015. The provided dataset contains information on the following: 

cow and lactation cycle: lactation number, date of calving, date of first record of calv in the alp, average quantity of milk (measured in kilograms).

Environmental conditions: Temperature Humidity Index (THI) averaged over 3 and 30 days, Cold Stress Index (CSI) averaged over 3 and 30 days, precipitation during Spring.

The average quantity of milk is the defined target column ("Y").

There were 41 null values found and thereby adjusting the DataFrame to 19,959 rows and 10 columns. Based on this adjusted DataFrame of non-missing values:
 - on average, a cow in this dataset produced 15.92 kg of milk.
 - The standard deviation of 4.08 kg suggests there is not a large variability in milk production among the cows.
 - The range of milk production is 3.5 kg to 40.37 kg per cow
 - Only 1 cow in the dataset had the lowest milk production of 3.5 kg  
 - Only 2 cows in the dataset had the highest milk production of 40.37 kg
 - 25th Percentile (13.07 kg): 25% of the cows produced less than 13.07 kilograms of milk. That equates to 
 - 50th Percentile (Median) (15.60 kg): 50% of the cows produce less than 15.60 kilograms of milk, and 50% produce more.
 - 75th Percentile (18.50 kg): 75% of the cows produce less than 18.50 kilograms of milk.



Visualizing the distribution of numeric columns:

![Histogram of Average Milk Yield](milk_histogram.svg)






2. Data Preprocessing:

Data Cleaning:
Handle missing values and outliers.
Encode categorical features if necessary.
Feature Engineering.
Normalize or standardize numerical features.
Prepare the data for training and testing.



Addendum No.1: References/Citations
Duruz, S., & Flury, C. (2020). Milk production and environmental conditions of mountain-pastured Braunvieh cows between 2000 and 2015 [Data set]. Zenodo. https://doi.org/10.5061/dryad.z612jm68g


