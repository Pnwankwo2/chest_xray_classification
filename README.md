# Milking the Data
![alt text](Resources/banner_image.jpg)
## Milk Production Prediction 
The Project Goal is to build an Artificial Neural Network (ANN) to accurately predict the average milk yield of cows based on environmental and lactation factors. The envirionmental factors are temperature, humidity, cold stress, precipitation. The lactation factors are lactation number, calving date, first record date

1. Dataset
Understanding the dataset:
cow and lactation cycle: lactation number, date of calving, date of first record of calv in the alp, average quantity of milk (measured in kilograms).
Environmental conditions: Temperature Humidity Index (THI) averaged over 3 and 30 days, Cold Stress Index (CSI) averaged over 3 and 30 days, precipitation during Spring.


Column name and description (Source:https://zenodo.org/records/3962046)

- newid: anonymised ID

- lact_num: lactation number (number of times the cow has calfed).

- calv_date: date of calving

- alp_date: date of the first record taken in the alp (usually shortly after the arrival of the animal in the alp)

- avg_milk: the average quantity of milk production in kilograms measured across three milking records
  
- avg_thi3: temperature humidity index, averaged over 3 days before the records, average over the 3 records taken in the alp

- avg_thi30: temperature humidity index, averaged over 30 days before the records, average over the 3 records taken in the alp

- avg_csi3: cold stress index, averaged over 3days before the records, average over the 3 records taken in the alp

- avg_csi30: tcold stress index, averaged over 30 days before the records, average over the 3 records taken in the alp

- avg_precspring: average precipitation during spring (April to July) of the year in which alping takes place, in mm/month

the average quantity of milk is the defined target column.

2. Data Preprocessing:

Data Cleaning:
Handle missing values and outliers.
Encode categorical features if necessary.
Feature Engineering.
Normalize or standardize numerical features.
Prepare the data for training and testing.



Addendum No.1: References/Citations


