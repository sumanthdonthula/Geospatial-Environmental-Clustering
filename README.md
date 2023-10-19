## Water Quality Prediction

## Sample Plots
![Sample Visualization](Sample%20Visualization.png)

**Sumanth Donthula**
**, Ashmita Gupta**

### Abstract

Water quality is a significant concern in India, with numerous states facing challenges in managing and maintaining clean water sources. To tackle this issue, machine learning algorithms are being employed to cluster states based on their water quality parameters. This study aims to cluster Indian states based on water quality data using machine learning algorithms. The dataset includes several water quality parameters such as pH, total dissolved solids, and hardness, among others. The data was preprocessed and scaled, and then k-means clustering was applied to the dataset. We have divided states into six clusters based on their water quality and air quality parameters. This study provides valuable insights into water quality in India and can aid policymakers in developing strategies to improve water quality in states with poor water quality.

### Overview

Water and air pollution are significant challenges in India, affecting the health and well-being of its citizens. According to the Central Pollution Control Board (CPCB), more than half of India's groundwater is contaminated with pollutants such as arsenic, fluoride, and iron, with states like Bihar, Uttar Pradesh, West Bengal, and Rajasthan having the worst water quality. India is also known for having some of the most polluted air in the world, with high levels of particulate matter, nitrogen dioxide, and sulfur dioxide. States like Delhi, Uttar Pradesh, Bihar, and West Bengal are among the worst affected.

The sources of water and air pollution in India are diverse and include industrial effluents, domestic sewage, agricultural runoff, and solid waste disposal for water pollution and vehicular emissions, industrial emissions, construction activities, and biomass burning for air pollution. Exposure to polluted water and air can cause severe health impacts, including respiratory diseases, cancer, neurological disorders, and developmental problems.

To address these issues, the Indian government has launched various initiatives, including the National Clean Air Programme (NCAP) and the Jal Jeevan Mission (JJM), to improve water and air quality. However, infrastructure inadequacy, inadequate enforcement of regulations, and a growing population continue to pose significant challenges to improving water and air quality in India.

### Objectives

- **Early detection of water contamination:** The model can be trained to detect contaminants in water at an early stage, which can help prevent widespread contamination and protect public health.
- **Water quality monitoring:** This model can be used to monitor water quality in real-time, allowing water treatment plants to take corrective action quickly if the water quality falls below acceptable levels.
- **Air quality monitoring:** This model can be used to monitor the air quality and provides information on the level of air pollution across different states in India.

### Data Collection & Processing

**Data Collection:** We collected water quality data that includes the values of environmental parameters (temperature, dissolved oxygen, pH, conductivity, BOD, Nitrate N + Nitrite N, Fecal Coliform, Total Coliform) from [CPCB Water Quality Data](http://www.cpcbenvis.nic.in/water_quality_data.html).

To support the features of water quality, we have extracted air quality data also to see if it adds some purpose while clustering from [CPCB Air Quality Data](http://www.cpcbenvis.nic.in/air_quality_data.html).

In total, we have **Water and Air Quality data** for the years 2017 to 2021 in the form of pdf files for each year. We collated all the pdfs and combined them into .xlsx files so that they can be processed in R.

**Data Processing:**

- **Data cleaning:** The data was in different formats for each year. We converted and processed the data in the same format so it's easy to process this file.

Most of our efforts in the project went into processing this file because it's not in a proper format with multiple sheets in excel. Moreover, each sheet has a particular feature. For example, in sheet1 PM2.5 values are there, and in sheet2 PM10 values are there.

Moreover, if we see there are blank values in the state and city because, for example, Bihar state is repeated twice in 4 and 5 rows, so the 5th row has a state value as blank. We need to fill this, and for each record, we are flagging its measure, which is present in column 5, and pivoting it via the mean of measures. Once this part is done, we are taking means and filling blank values in our data frame.

We have merged Water Quality of Data with Air Quality data based on state, city, and year.

### Data Analysis

We will present Analysis for 2017 Data, and we have done the same analysis for the rest of the years. We have got Water quality features like minimum and maximum values; we have averaged them and used while using clustering.

**Exploratory Data Analysis (EDA):**

Visualizing the data for all features in the dataset, including Water and Air Quality Features.

We can observe that most of the attributes are normally distributed, and some attributes are skewed. Anyway, we will perform scaling before using clustering models.

**Obtaining the covariance matrix:**

We can see that Total Coliform Avg and Fecal Coliform Avg are the same, and PM2.5, NO2 are highly correlated. So, we will remove those columns for further processing.

**Performing PCA for 2017 Data:**

The first 4 principal components explain 77% of the Variance in Data.

### Clustering

For water and air quality analysis in Indian states, we used k-means clustering to group states based on their water quality parameters.

**Step 1:** We started by selecting the relevant water and air quality parameters, such as pH, total dissolved solids, and the concentration of various contaminants.

**Step 2:** We then used k-means clustering for grouping states based on air & water parameters in datasets.

**Step 3:** We got 6 clusters on our filtered dataset using K means clustering.

**Step 4:** Then once the clusters were formed, we assigned ranks to the clusters based on their features like Fecal Coliform, BOD, Dissolved O2, PM10, PM2.5, and NO2 to give meaning to these clusters. We took a reference of below criteria that is ideal for checking water quality:

- **Designated-Best-Use**
- **Class of water**
- **Criteria**

| Criteria                                       | Total Coliforms Organism MPN/100ml shall be 50 or less |
|-----------------------------------------------|--------------------------------------------------------|
| pH between 6.5 and 8.5                        | Drinking Water Source without conventional treatment but after disinfection                                       |
| Outdoor bathing (Organised)                   | Dissolved Oxygen 6mg/l or more |
| Biochemical Oxygen Demand 5 days 20C 2mg/l or less | Total Coliforms Organism MPN/100ml shall be 500 or less |
| pH between 6.5 and 8.5 | Dissolved Oxygen 5mg/l or more |

K-means clustering can provide valuable insights into the water quality status of Indian states, such as identifying states with similar water quality profiles or identifying states with poor water quality that require immediate attention. However, like any clustering technique, the interpretation of results should be done with caution, and additional domain knowledge and contextual information should be taken into account. We have performed K Means clustering with 6 clusters on our filtered dataset. Then once the clusters are formed, as we have assigned ranks to the clusters based on their features like Fecal Coliform, BOD, Dissolved O2, PM10, PM2.5, and NO2.

### Year On Year Analysis

We have done the same procedure for 5 years of data and obtained the following results via clustering.

### Conclusion

We had data from 16 states available. Further, we have clustered states based on their water and air quality.

Two key observations:

- We can see that from 2017 most of the states are performing better in terms of water and air quality.
- We observed that Chandigarh and Haryana are performing very poorly in terms of water and air quality, and some action should be taken by government authorities to clean up the water.

### References

**Academic Papers:**

1. [Link to Academic Paper 1](https://pdxscholar.library.pdx.edu/cgi/viewcontent.cgi?article=1002&context=reu_reports)
2. [Link to Academic Paper 2](https://www.researchgate.net/publication/351077205_Efficient_Water_Quality_Prediction_for_Indian_Rivers_Using_Machine_Learning)
3. [Link to Academic Paper 3](https://www.mdpi.com/2306-5338/9/5/92)

**Articles:**

1. [Link to Article 1](https://www.datascience2000.in/2021/10/water-quality-prediction-using-machine.html)
2. [Link to Article 2](https://www.researchgate.net/publication/361118196_The_Quality_of_Drinkable_Water_using_Machine_Learning_Techniques)
3. [Link to Article 3](https://www.sciencedirect.com/science/article/abs/pii/S0022169419308194)

**Existing projects:**

- [Kaggle Project 1](https://www.kaggle.com/code/maujmishra/water-quality-index-prediction)
- [Kaggle Project 2](https://www.kaggle.com/code/imakash3011/water-quality-prediction-7-model/notebook)

**Reference Books:**

- "Machine Learning Techniques for Water Quality Monitoring" by Yuanyuan Liu, Yongping Li, and Junfeng Ji
- "Machine Learning for Environmental Monitoring" by Michael G. Schrlau and Kalyanmoy Deb
- Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani. An Introduction to Statistical Learning: with Applications in R. New York: Springer, 2013. Print
