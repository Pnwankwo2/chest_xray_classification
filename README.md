# Milking the Data
![alt text](Resources/banner_image.jpg)

## Milk Production Prediction 
The Project Goal is to build an Artificial Neural Network (ANN) to accurately predict the average milk yield of cows based on environmental conditions (temperature, humidity, cold stress, precipitation) and lactation cycle information (lactation number, calving date, first record date). 

1. Dataset

The dataset has been extracted from the milk record database of the Braunvieh-CH breeding organisation, from [(Zenodo record)](https://zenodo.org/records/3962046) (Duruz, S., & Flury, C. (2020). The Rights of the dataset is cc0-1.0 icon Creative Commons Zero v1.0 Universal, making it freely usable without restriction. The dataset meets encoding to UT-8 standard. 

The dataset encompasses 20,000 cows and includes 10 variables, therefore represented as a DataFrame with 20,000 rows and 10 columns. The data spans a period from years 2000 to 2015. The provided dataset contains information on the following: 

cow and lactation cycle: lactation number, date of calving, date of first record of calv in the alp, average quantity of milk (measured in kilograms).

Environmental conditions: Temperature Humidity Index (THI) averaged over 3 and 30 days, Cold Stress Index (CSI) averaged over 3 and 30 days, precipitation during Spring.

The average quantity of milk is the defined target column ("Y").

There were 41 null values found which adjusted the DataFrame down from 20,000 to 19,959 rows, and 10 columns. Based on the adjusted DataFrame of non-missing values, the following observations were made of the histogram of the target column ("Y") of the distribution of Average Milk Production over the three milk records:
 - The distribution is positively skewed to the right:
 - as a smaller number of data points extend further to the right side of the x-axis, creating a longer tail; 
 - and since the average milk yield for all cows is 15.92 kg which is more than the median (middle) milk yield of 15.6 kg. 
 - The most frequently produced milk production value (mode) of any one cow is 14.6 kg.
 - The standard deviation of 4.08 kg suggests there is not a large variability in milk production among the cows
 - The data is relatively spread out with a wide range of milk production values from 3.5 kg to 40.37 kg per cow
 - Only 1 cow in the dataset had the lowest milk production of 3.5 kg  
 - Only 2 cows in the dataset had the highest milk production of 40.37 kg being the outliers at the higher end of the distribution
 - 25% of the cows (4,981) produced less than 13.07 kilograms of milk.  
 - 50% of the cows (10,000) produced less than 15.60 kilograms of milk, and 50% (10,000) produce more.
 - 75% of the cows (14,992) produced less than 18.50 kilograms of milk.
 - 3,753 cows (approximately 68.9%) fall within one standard deviation of the mean
 - 19,067 cows (approximately 95.5%) fall within two standard deviations of the mean.

Based on these observations, it can be inferred that a majority of the cows in the dataset have an average milk yiled between 15 - 20 kgs over the three milk records. An investigation of the cow (ID 3844) with the exceptionally low milk yiled of 3.5kgs and an investigation of the two cows (ID 3923 and ID 6922) with the exceptionally high milk yield of 40.37 kg can be done by calculating and analyzing a correlation matrix of all the variables in the dataset and assuming all other things not known from the dataset are normal (health, nutrition, feeding management, reproduction, genetics, and the like).

In summary of understanding a correlation matrix, 
- correlation coefficients range from -1 to 1.
- A value of 1 indicates a perfect positive correlation (as one variable increases, the other increases proportionally).
- A value of -1 indicates a perfect negative correlation (as one variable increases, the other decreases proportionally).
- A value of 0 indicates no correlation between the variables.

We have inferred the following from the correlation matrix of the coorelation between variables in the dataset: 

lactation number (lact_num):

Has a weak positive correlation with avg_thi3 (0.24). This suggests that cows with higher lactation numbers (likely older cows) might have slightly higher average THI3 values.
avg_milk:

Shows strong negative correlations with avg_thi3 (-0.33), avg_csi3 (-0.17), avg_thi30 (-0.27), and date_diff (-0.52). This indicates that cows with higher average milk production tend to have lower values for these variables.
A positive correlation with avg_precspring (0.16) suggests that higher average spring precipitation might be associated with slightly higher milk production.
avg_thi3:

Has strong negative correlations with avg_csi3 (-0.83), avg_thi30 (-0.77), and date_diff (0.55). This suggests that avg_thi3 is strongly related to these variables.
avg_csi3:

Shows high positive correlations with avg_thi30 (0.69) and avg_thi3 (-0.83). This indicates a strong relationship between these cold stress indices.
avg_csi30:

Also shows high positive correlations with avg_thi3 (-0.77) and avg_csi3 (0.69).
avg_precspring:

Has a moderate positive correlation with date_diff (0.28). This suggests that cows with longer intervals between calving and the start of the alping season might have experienced higher average spring precipitation.
date_diff:

Shows a strong positive correlation with avg_thi3 (0.55), avg_csi3 (0.33), and avg_csi30 (0.42). This suggests that cows with longer intervals between calving and the start of the alping season tend to have higher cold stress indices.
calv_month:

Shows strong positive correlations with avg_thi3 (0.68), avg_csi3 (0.43), avg_csi30 (0.54), and date_diff (0.66). This suggests that cows calving in certain months might experience higher cold stress.
calv_day_of_month, alp_month, alp_day_of_month: These variables show relatively weak correlations with other variables.







2. Data Preprocessing:

Data Cleaning:
Handle missing values and outliers.
Encode categorical features if necessary.
Feature Engineering.
Normalize or standardize numerical features.
Prepare the data for training and testing.



Addendum No.1: References/Citations
Duruz, S., & Flury, C. (2020). Milk production and environmental conditions of mountain-pastured Braunvieh cows between 2000 and 2015 [Data set]. Zenodo. https://doi.org/10.5061/dryad.z612jm68g


