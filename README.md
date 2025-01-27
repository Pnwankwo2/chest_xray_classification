# Milking the Data
![alt text](Resources/banner_image.jpg)

## Milk Production Prediction 
The Project Goal is to build an Artificial Neural Network (ANN) to accurately predict the average milk yield of cows based on environmental conditions (temperature, humidity, cold stress, precipitation) and lactation cycle information (lactation number, calving date, first record date). 

1. **Data Exploration**

**Braunvieh-CH Dairy Herd Dataset**

The dataset has been extracted from the milk record database of the Braunvieh-CH breeding organisation, from [(Zenodo record)](https://zenodo.org/records/3962046) (Duruz, S., & Flury, C. (2020).  Braunvieh is a type of brown cattle originating in Switzerland. CH is the latin words "Confoedaratio Helvetica", meaning Swiss Confederation. The dataset is freely available under a CC0 1.0 Universal license, permitting unrestricted use. Encoded in UTF-8 format, the dataset encompasses information on 20,000 cows across 10 variables, presented in a DataFrame with 20,000 rows and 10 columns. The data covers a period ranging from the year 2000 to 2015.

The dataset includes details on the following aspects of the cows:

**Lactation cycle**: lactation number, date of calving, date of the first milking record during the Alpine grazing season, and average milk yield (in kilograms).

**Environmental factors**: Temperature Humidity Index (THI) averaged over 3 and 30 day periods, Cold Stress Index (CSI) averaged over 3 and 30 day periods, and precipitation levels during spring.

The average milk yield was designated as the target variable ("Y") as the objective is to predict future milk production.

After eliminating 41 missing values, the DataFrame was reduced to 19,959 rows and 10 columns. Analyzing the distribution of the target variable ("Y"), representing average milk yield across the three milking records, revealed the following:

The distribution exhibits a positive skew, characterized by a greater number of data points concentrated on the right side, resulting in a longer tail. This indicates that a smaller number of cows produced significantly more milk compared to the majority of the cows in the dataset.

The average milk yield across all cows is 15.92 kg, exceeding the median (middle) milk yield of 15.6 kg, which is a more representative measure in the presence of a skewed distribution.

The most frequently produced milk yield for any individual cow was 14.6 kg, representing the mode of the data.

The standard deviation of 4.08 kg suggests that there is not a substantial variation in milk production among the cows.

The data exhibits a relatively broad spread, encompassing a wide range of milk yield values from 3.5 kg to 40.37 kg per cow.

Only one cow in the dataset displayed the lowest milk production of 3.5 kg, constituting an outlier on the lower end of the distribution.

Just two cows within the dataset demonstrated the highest milk production of 40.37 kg, representing outliers at the upper end of the distribution.

25% of the cows (4,981) produced less than 13.07 kilograms of milk.

50% of the cows (10,000) produced less than 15.60 kilograms of milk, while the other 50% (10,000) produced more.

75% of the cows (14,992) produced under 18.50 kilograms of milk.

Approximately 68.9% (13,753 cows) fell within one standard deviation of the mean milk yield.

Approximately 95.5% (19,067 cows) fell within two standard deviations of the mean milk yield.

Approximately 99.53% (19,865 cows) fell within three standard deviations of the mean milk yield.

Based on these observations, it can be inferred that a substantial portion of the cows in the dataset exhibit an average milk yield ranging between 15 and 20 kilograms over the three milk records.

**Investigating Extreme Milk Yield Cases**

To understand the factors contributing to the exceptionally low milk yield of cow ID 3844 (3.5 kg) and the exceptionally high yield of cows ID 3923 and ID 6922 (both at 40.37 kg), we analyzed the relationships between various factors and milk production using a correlation matrix which provided valuable insights into these potential relationships.

**Correlation Matrix Overview**

**Correlation coefficients range from -1 to 1**:

 1.00: Perfect positive correlation (as one variable increases, the other increases proportionally).
-1.00: Perfect negative correlation (as one variable increases, the other decreases proportionally).
 0.00: No correlation between the variables.
The diagonal of the correlation matrix (top-left to bottom-right) always shows correlations of each variable with itself, which are 1.00.

**Key Correlations Observed**

**Lactation Number (lact_num)**: Shows a weak positive correlation with avg_thi3 (0.24), suggesting that older cows (with higher lactation numbers) might experience slightly higher average THI3 values.

**Average Milk Production (avg_milk)**:
Exhibits strong negative correlations with avg_thi3 (-0.33), avg_csi3 (-0.17), avg_thi30 (-0.27), and date_diff (-0.52). This indicates that cows with higher average milk production tend to have lower values for these variables.
Shows a positive correlation with avg_precspring (0.16), suggesting that higher average spring precipitation might be associated with slightly higher milk production.

**Temperature Humidity Index averaged over 3 day period (avg_thi3)**: Exhibits strong negative correlations with avg_csi3 (-0.83), avg_thi30 (-0.77), and date_diff (0.55), indicating strong relationships between these variables.

**Cold Stress Index averaged over 3 day period (avg_csi3)**: Exhibits a strong negative correlation with avg_thi3 (-0.83) and a high positive correlation with avg_thi30 (0.69), indicating a strong relationship between these temperature and cold stress indices.

**Cold Stress Index averaged over 30 day period (avg_csi30)**: Shows high positive correlations with avg_thi3 (-0.77) and avg_csi3 (0.69), further emphasizing the interconnectedness of these variables.

**Average Spring Precipitation (avg_precspring)**: Has a moderate positive correlation with date_diff (0.28), suggesting that cows with longer intervals between calving and the start of the Alpine grazing season might have experienced higher average spring precipitation.

**Interval Between Calving and Alpine Grazing (date_diff)**: Shows strong positive correlations with avg_thi3 (0.55), avg_csi3 (0.33), and avg_csi30 (0.42), suggesting that cows with longer intervals between calving and the start of the Alpine grazing season tend to have higher cold stress indices.

**Calving Month (calv_month)**: Exhibits strong positive correlations with avg_thi3 (0.68), avg_csi3 (0.43), avg_csi30 (0.54), and date_diff (0.66), suggesting that cows calving in certain months might experience higher cold stress.

**Calving Day of Month (calv_day_of_month), Alpine Grazing Month (alp_month), Alpine Grazing Day of Month (alp_day_of_month)**: These variables showed relatively weak correlations with other variables in the dataset.

Overall, the correlation matrix primarily highlights potential associations between milk production, cold stress indices, calving season, and the interval between calving and the start of the Alpine grazing season.

**Potential Factors Influencing Extreme Milk Yields**

Based on the observed correlations, potential reasons for cow ID 3844's exceptionally low milk yield (3.5 kg) include:

**Environmental Stress**:

**High Temperature and Humidity (THI)**: While the given THI of 59.18 might not seem excessively high, prolonged exposure to high temperatures and humidity can negatively impact milk production.

**Cold Stress**: The high cold stress index (CSI) values (1095.81 and 1040.56) suggest the cow may have experienced significant cold stress, which can reduce milk production.

**Heat Stress**: Although less likely with the given THI, heat stress during lactation could have significantly reduced milk production.

**Shorter-than-Ideal Dry Period**: The 277-day interval from calving to the first record might suggest a shorter dry period, which could have negatively impacted subsequent lactation.

For cows ID 3923 and ID 6922, which exhibited exceptionally high milk yield (40.37 kg), potential contributing factors include:

**Optimal Environmental Conditions**:

**Mild Climate**: The relatively low THI values (44.27) suggest a comfortable temperature and humidity environment, minimizing heat stress and potentially optimizing milk production.

**Moderate Cold Stress**: While cold stress can negatively impact milk production, the CSI values (1088.68 and 1140.58) might indicate a moderate level of cold stress, which could potentially stimulate feed intake and milk production in some breeds.

**Adequate Forage**: The average spring precipitation of 182.88 mm/month suggests sufficient rainfall for good pasture growth, providing the cow with ample high-quality forage for milk production.

**Shorter Calving-to-Alpine Grazing Interval**: The short interval of 11 days between calving and the start of the Alpine grazing period might have positively influenced milk production in these cows. However, this can vary depending on the individual cow and breed.

**Important Considerations**:

**Correlation vs. Causation**: It is crucial to remember that correlation does not imply causation. Further analysis, such as regression analysis, is necessary to determine the causal relationships between these variables.

**Data Limitations**: The provided data represents a snapshot of the cow's condition and environment. Factors such as the cow's health, nutrition, feeding management, reproduction, genetics, age, breed, and previous lactation history can significantly influence milk production and are not included in this dataset.

**Need for Further Investigation**: To determine the specific reasons for low or high milk production in these cows, further investigation is necessary. This could include examining the cow's medical history, feeding records, and environmental conditions more thoroughly. Long-term monitoring of various factors, including feed intake, body condition score, and reproductive health, is also crucial for a more comprehensive understanding.

2. **Data Preprocessing**:

Data Cleaning:
Handle missing values and outliers.
Encode categorical features if necessary.
Feature Engineering.
Normalize or standardize numerical features.
Prepare the data for training and testing.



**Addendum No.1: References/Citations**

Duruz, S., & Flury, C. (2020). Milk production and environmental conditions of mountain-pastured Braunvieh cows between 2000 and 2015 [Data set]. Zenodo. https://doi.org/10.5061/dryad.z612jm68g
 


