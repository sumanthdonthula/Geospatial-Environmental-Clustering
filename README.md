<a name="br1"></a> 

**Water Quality Prediction**

**CSP 571 Final Report**

**Sumanth Donthula**

**Ashmita Gupta**

A20519856

A20512498

1



<a name="br2"></a> 

**Abstract**

Water quality is a significant concern in India, with numerous states facing

challenges in managing and maintaining clean water sources. To tackle this

issue, machine learning algorithms are being employed to cluster states based

on their water quality parameters. This study aims to cluster Indian states based

on water quality data using machine learning algorithms. The dataset includes

several water quality parameters such as pH, total dissolved solids, and

hardness, among others. The data was preprocessed and scaled, and then k-

means clustering was applied to the dataset. We have divided states into six

clusters based on their water quality and air quality parameters. This study

provides valuable insights into water quality in India and can aid policymakers

in developing strategies to improve water quality in states with poor water

quality.

**1. Overview**

Water and air pollution are significant challenges in India, affecting the health and well-being of its

citizens. According to the Central Pollution Control Board (CPCB), more than half of India's

groundwater is contaminated with pollutants such as arsenic, fluoride, and iron, with states like Bihar,

Uttar Pradesh, West Bengal, and Rajasthan having the worst water quality. India is also known for

having some of the most polluted air in the world, with high levels of particulate matter, nitrogen

dioxide, and sulfur dioxide. States like Delhi, Uttar Pradesh, Bihar, and West Bengal are among the

worst affected.

The sources of water and air pollution in India are diverse and include industrial effluents, domestic

sewage, agricultural runoff, and solid waste disposal for water pollution and vehicular emissions,

industrial emissions, construction activities, and biomass burning for air pollution. Exposure to

polluted water and air can cause severe health impacts, including respiratory diseases, cancer,

neurological disorders, and developmental problems.

To address these issues, the Indian government has launched various initiatives, including the National

Clean Air Programme (NCAP) and the Jal Jeevan Mission (JJM), to improve water and air quality.

However, infrastructure inadequacy, inadequate enforcement of regulations, and a growing population

continue to pose significant challenges to improving water and air quality in India.

**2. Objectives:**

• **Early detection of water contamination:** The model can be trained to detect contaminants in

water at an early stage, which can help prevent widespread contamination and protect public health

• **Water quality monitoring**: This model can be used to monitor water quality in real-time, allowing

water treatment plants to take corrective action quickly if the water quality falls below acceptable

levels

• **Air quality monitoring:** This model can be used to monitor the air quality and provides

information on the level of air pollution across different states in India

2



<a name="br3"></a> 

**3. Data Collection & Processing**

**Data Collection:** We collected water quality data that includes the values of environmental parameters

(temperature, dissolved oxygen, pH, conductivity, BOD, Nitrate N + Nitrite N, Fecal Coliform, Total Coliform)

from <http://www.cpcbenvis.nic.in/water_quality_data.html>

•

•

•

To Support the features of water quality we have extracted air quality data also to see if it adds some

purpose while clustering from <http://www.cpcbenvis.nic.in/air_quality_data.html>

In total, we have **Water and Air Quality data** for the years 2017 to 2021 in the form of pdf files for

each year

We collated all the pdfs and combined them into .xlsx files so that they can be processed in R.

**Data Processing:**

**Snapshot of Air Quality Data:**

**Data cleaning**: The data was in different formats for each year. We converted and processed the data

in the same format so it’s easy to process this file.

**Snapshot of Air Quality Data:**

Most of our efforts in the project went into processing this file because its not in a proper format with

multiple sheets in excel. More over each sheet have particular feature for example in sheet1 PM2.5

values are there and in sheet2 PM10 values are there.

3



<a name="br4"></a> 

Moreover, if we see there are blank values in state and city because for example Bihar state is repeated twice in 4

and 5 rows so, the 5 row has state value as blank. We need to fill this and for each record we are flagging it’s

measure which is present in column 5 and pivoting it via mean of measures. Once this part is done we are taking

means and filling blank values in our data frame.

We have merged Water Quality of Data with Air Quality data based on state, city and year.

**4. Data Analysis**

We will present Analysis for 2017 Data and we have done the same analysis for rest of the years. We have got

Water quality features like minimum and maximum values, we have averaged them and used while using

clustering.

Exploratory Data Analysis (EDA):

Visualizing the data for all features in the dataset including Water and Air Quality Features.

4



<a name="br5"></a> 

5



<a name="br6"></a> 

6



<a name="br7"></a> 

We can observe that most of the attributes are normally distributed, and some attributes are skewed.

Anyways, we will perform scaling before using clustering models.

Obtaining the covariance matrix:

We can see that Total Coliform Avg and Fecal Coliform Avg are same and PM2.5, NO2 are highly

7



<a name="br8"></a> 

correlated. So, we will remove those columns for further processing.

**Performing PCA for 2017 Data:**

The first 4 principal components explain 77% of the Variance in Data.

**5. Clustering**

For water and air quality analysis in Indian states, we used use **k-means clustering** to group

states based on their water quality parameters.

**Step 1:** We started by selecting the relevant water and air quality parameters, such as pH, total

dissolved solids, and concentration of various contaminants.

**Step 2:** We then used k-means clustering for grouping states based on air & water parameters

in datsets

**Step 3:** We got with 6 clusters on our filtered dataset using K means clustering

**Step 4:** Then once the clusters were formed, we assigned ranks to the clusters based on their

features like Fecal Coliform, BOD, Dissolved O2, PM10, PM2.5 and NO2 to give a meaning

to these clusters. We took a reference of below criteria that is ideal for checking water quality:

8



<a name="br9"></a> 

**Designated-Best-Use**

**Class of water**

**Criteria**

Total Coliforms Organism MPN/100ml shall be 50 or

less

pH between 6.5 and 8.5

Drinking WaterSource

without conventional

treatment but after

disinfection

A

Dissolved Oxygen 6mg/l or more

Biochemical Oxygen Demand 5 days 20C 2mg/l or less

Total Coliforms Organism MPN/100ml shall be 500 or

less pH between 6.5 and 8.5 Dissolved Oxygen 5mg/l

or more

Outdoor bathing

(Organised)

B

C

Biochemical Oxygen Demand 5 days 20C 3mg/l or less

Total Coliforms Organism MPN/100ml shall be 5000

or less pH between 6 to 9 Dissolved Oxygen 4mg/l or

more

Drinking water source after

conventional treatment and

disinfection

Biochemical Oxygen Demand 5 days 20C 3mg/l or less

pH between 6.5 to 8.5 Dissolved Oxygen 4mg/l or

more

Free Ammonia (as N) 1.2 mg/l or less

pH betwwn 6.0 to 8.5

Electrical Conductivity at 25C micro mhos/cm

Max.2250

Propagation of Wild life and

Fisheries

D

E

F

Irrigation, Industrial Cooling,

Controlled Waste disposal

Water not suitable for any

purpose

Total Coliforms Organism greater than 5000 and pH is

high

K-means clustering can provide valuable insights into the water quality status of Indian states,

such as identifying states with similar water quality profiles or identifying states with poor

water quality that require immediate attention. However, like any clustering technique, the

interpretation of results should be done with caution, and additional domain knowledge and

contextual information should be taken into account.We have performed K Means clustering

with 6 clusters on our filtered dataset. Then once the cluster are formed bas we have assigned

ranks to the clusters based on their features like Fecal Coliform,BOD, Dissolved O2, PM10,

PM2.5 and NO2.

9



<a name="br10"></a> 

We have obtained the following clusters:

We have performed hierarchical clustering using ward’s distance and we obtained same results

with 6 clusters.

10



<a name="br11"></a> 

**Year On Year Analysis:**

We have did the same procedure for 5 years of data and obtained the following results via

clustering.

11



<a name="br12"></a> 

12



<a name="br13"></a> 

**Conclusion:**

We had data from 16 states available. Further, we have clustered states based on their water and air quality.

Two key observations:

• We can see that from 2017 most of the states are performing better in terms of water and air

quality.

• We observed that Chandigarh and Haryana are performing very poor in terms of water and air

quality and some action should be taken by government authorities to clean up the water

13



<a name="br14"></a> 

**References**

Academic Papers:

1\. [https://pdxscholar.library.pdx.edu/cgi/viewcontent.cgi?article=1002&context=reu](https://pdxscholar.library.pdx.edu/cgi/viewcontent.cgi?article=1002&context=reu_reports)

[_reports](https://pdxscholar.library.pdx.edu/cgi/viewcontent.cgi?article=1002&context=reu_reports)

2\. [https://www.researchgate.net/publication/351077205_Efficient_Water_Quality_Pr](https://www.researchgate.net/publication/351077205_Efficient_Water_Quality_Prediction_for_Indian_Rivers_Using_Machine_Learning)

[ediction_for_Indian_Rivers_Using_Machine_Learning](https://www.researchgate.net/publication/351077205_Efficient_Water_Quality_Prediction_for_Indian_Rivers_Using_Machine_Learning)

3\. <https://www.mdpi.com/2306-5338/9/5/92>

Articles:

1\. https://www.datascience2000.in/2021/10/water-quality-prediction-using-

machine.html

2\. https://www.researchgate.net/publication/361118196\_The\_Quality\_of\_Drinkable\_

Water\_using

\_Machine\_Learning\_Techniques

•

https://www.sciencedirect.com/science/article/abs/pii/S002216941930819

4

•

•

•

Existing projects:

https://www.kaggle.com/code/maujmishra/water-quality-index-prediction

https://www.kaggle.com/code/imakash3011/water-quality-prediction-7-

model/notebook

•

•

Reference Books:

"Machine Learning Techniques for Water Quality Monitoring" by Yuanyuan Liu,

Yongping Li, and

•

•

Junfeng Ji

"Machine Learning for Environmental Monitoring" by Michael G. Schrlau and

Kalyanmoy Deb.

•

•

Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani. An Introduction

to Statistical

Learning : with Applications in R. New York :Springer, 2013. Print

14

