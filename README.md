# KBS PROJECT 
<br>

<h1> Rain Prediction and Draught Analysis for Australia </h1> <br>


<h2>1) Research question </h2><br>
<p>What is the group trying to learn or question to answer?  Who is interested (audience)? </p><br>
<p> We are predicting whether it will rain or not tomorrow by using machine learning algorithms such as Logistic regression and KNN models. People who plan their day according to weather conditions will be strongly benefitted. It will also help people whether to carry an umbrella or not. <br>
 
<h2> 2) Domain and Data: Identify domain and source(s) of data </h2>
	<p>Domain: Weather forecasting. Precisely to predict whether it will rain tomorrow or not? </p>
  <p>Source: The dataset we took is from Kaggle and the link to the dataset is https://www.kaggle.com/jsphyg/weather-dataset-rattle-package</p>
<br>

<h3>a) Preprocessing that may be necessary </h3> 
<p>Preprocessing mainly comprises of cleaning the dataset and eliminating the columns which won’t be imperative to the prediction of the target feature. For our dataset, we will be implementing following steps to clean our dataset for effective accuracy:<p><br>
1.Null-value elimination<br>
2.Removing Outliers<br>
3.Categorical to numerical conversion<br>
4.Review correlation matrix for checking the relation between columns<br>
<p>Further more we’ll be assessing the columns which won’t be having a lot of importance and try to eliminate them. Some of the columns contains similar type of information and if it made the model work faster we might integrate their data into a single column.</p><br>

<h3>b)Size of Data:</h3>
<P>This dataset contains daily weather observations from numerous Australian weather stations and it has 142k rows over 24 columns which describe various factors that contribute in rainfall prediction.<br>
 
<h3>c)Tentative plan for analysis on GCP</h3><br>

<h4>i. EDA and preprocessing:</h4>
<p>The preprocessing part involves observing columns and their importance in order to predict if it’s going to rain tomorrow or not. We’ll be getting rid of columns which doesn’t contribute to the prediction and keeping those which will make an impact when selected as features for the model. Exploratory data analysis will involve visualizing the dataset by using different features form the dataset. To name some we can create a graph for location distribution of the rain then we can analyze if the location column plays an important role in predicting our target feature. Other features such as WinDir3pm or WinDir9pm can also be used to create a distribution graph to observe the difference and infer observations from that.</p>

<h4>ii. Dashboard for User group, Dashboard for Data Engineers:</h4>
<p>Dashboard for user will consist of basic graphs such as a donut graph depicting rain today variation (yes or no). The aim of the dashboard will be to convey less complex information in terms of visuals so that one can easily correlate between different features used to predict the target variable. Dashboards for Data Engineers will have graphs depicting correlation b/w different features and what can be used as a dominant feature for prediction and what can be ignored. The crux of this process would be assessing the dashboard and the graphs and proper knowledge about the database.</p>

<h4>iii. GCP further processing - ML:</h4>
<p>GCP will be used to run the models using pyspark. We’ll be using both datalab and ssh terminal to try and run the models. Our definite goal is to run Logistic regression and KNN models on the dataset. If we’re successfully able to do that, we would be to try running more complex model such as decision tree or random forest to learn in-depth about running machine learning model in GCP.</p>

<h4>iv. Evaluating the result:</h4>
<p>We’ll be running two models, Logistic Regression and KNN on the given dataset.     In order to evaluate the result of these two model and how good are they at predicting the target variable we’ll be using different measure to calculate the effectiveness of a model such as accuracy score, recall score or its precision. We’ll be comparing all the values for the said models and give a result as to which model works better for the current dataset.</p> 

<h4>v. Steps for production model:</h4>
<p>The models that we’ll be training on the dataset- Logistic Regression, and KNN will be deployed using DataFlow. The dataset will be read using BigQuery, then for every record, model prediction will be carried out, and the results are written back to BigQuery. </p>

<h4>vi. Final Dashboard for the User:</h4>
<p>The final dashboard will consist of predicted data in form of a graph and it will depict the results of different model. The dashboard will also have a graph showing the model used along with their evaluating score. </p>


<p>At this stage we have already completed the steps 1 and 2 from our plan that is to create teh dashboards from user perspective and data analyst perspective. We have also completed the pre-processing of our dataset and EDA. We will from now on be focusing on the further steps to complete the project succesfully by predicting whether it will rain tomorrow or not accurately. </p>
<br><br>

<h2><p> 3) Dashboard <br> </h2>
<br>Screenshot of the dashboard created in Google Cloud Platform - Data Studio: <br> <br>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/dashboard_img_1.png)

<br><br>

Screenshots of EDA done using Python in Google Cloud Platform - Data Flow for User<br><br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/EDAForUsers.png)
<br>
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/EDAForUsers(1).png)

<br><br>
Screenshots of EDA done using Python in Google Cloud Platform - Data Flow for Analyst<br><br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/EDAForAnalyst(2).png)
<br>
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/EDAForAnalyst(3).png)
<br>
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/EDAForAnalyst(4).png)

<br><br>

<h2><p> 4) Adding new features to the dataset:</h2><br>

<p> We have added 4 new features to our dataset namely: Altitude, MoonPhase, Longitude and Latitude. The changes were so small that it made only .01 difference in the whole prediction. Upon researching more about the dataset we have added MoonPhase paramemeter, we observed that there were not so demonstrated changes in the prediction as out dataset was already using lot of important parameters used in predicting rain and MoonPhase did not have greater weightage than them. So we use MoonPhase field in our prediction and run the previous models as mentioned above again including the MoonPhase field in our dataset. Our motive was to learn more about the google cloud and see how we can add the moonphase attribute into the dataset. Upon doing that, we ran the models again on the dataset as talked earlier and compared the accuracy we got from both the models. We also added altitude, latitude and longitude but again they did not provide much information about the changes or the effects on rainfall. <p><br>
	
<p> We might be wondering what MoonPhase is so let us dive deep into what it means. <p><br>
	
<p> The moon is said to influence the chances of rainfall. When the moon is high in the sky, it creates bulges in the planet's atmosphere that creates imperceptible changes in the amount of rain that falls below. <br>
Also, the new University of Washington research to be published in Geophysical Research Letters shows that the lunar forces affect the amount of rain - though very slightly. Tsubasa Kohyama, a UW doctoral student in atmospheric sciences and John Wallace, UW professor of atmospheric sciences have studied the changes in Air pressure with change in phases of the moon. When the moon is overhead, its gravity causes Earth's atmosphere to bulge toward it, so the pressure or weight of the atmosphere on that side of the planet goes up. High pressure increases the temperature of air parcels below. Since warmer air can hold more moisture, the same air parcels are now farther from their moisture capacity. The change is only about 1 percent of the total rainfall variation, though, not enough to affect other aspects of the weather or for people to notice the difference. Instead, this effect could be used to test climate models, he said, to check if their physics is good enough to reproduce how the pull of the moon eventually leads to less rain. Though the researches are still exploring the topic to see whether certain categories of rain, like heavy downpours, are more susceptible to the phases of the moon, and whether the frequency of rainstorms shows any lunar connection.<p><br>
	
<p> Moving ahead we notice that Australia is a drought prone continent. It has seen a lot of draught over the years and some of the cities experienced very less rainfall when compared to others. From the dataset, we already have the amount of rainfall of a particular city that experienced rainfall for a particular year. From that, we were able to see which cities had a greater rainfall when compared to others. We came up with two visualizations to support our case. <p> <br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/droughtimg1.jpg)

<br> 
<p> The visualization above shows the distribution of rainfall according to different cities. It can be seen that Cobar has the least amount of rainfall observed over the year. Since it is a drought prone continent, it makes sense to look over the cities which has a lesser rainfall as they are more prone to be affected by the drought. Upon analyzing more and going through more datasets pertaining to rainfall in Australia it was found that the lowest amount of rainfall was observed during the years 2008-2009. This is the time when Australia observed it's most hottest season. If we look at the above visualization, we can analyze that during these times, cities like Cobar needed more attention as it was most affected by it. <p>
<br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/droughtimg2.jpg)

<br>
<p> The climatic pattern of Australia doesn’t indicate anything substantial and it keeps on changing. To acknowledge that, We tried looking into some more data related to climate of Australia and got to know about the historical pattern. There are lot of maps and graphs available to public on Australian government website which were used to analyze more about the weather and climate conditions in Australia. <p><br>

<h3><p> Effect of Rainfall in Drought prediction:<p><br></h3>

<p>The report shows the studies of the weather and compares rainfall period with the long-term average, and then projects if it is below average and by how much.

We see that eastern Australia has been experiencing drier weather than normal conditions since 2013, despite reasonable rainfall in 2016.<p>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/rainfallmaps.jpeg)

<br>
<h3><p>Observations:<p></h3><br>

<p>The research shows a change in rainfall patterns in Australia in the past century:

<P>- It was found that the most recent period, the rainfall in the south is quite unusual – there seems to be less rainfall, especially during the cool season.
- The other observation was that, the northern Australia was getting wetter than ever before in the warm season specifically.<P><br>

<p>Below is the timeline shows the annual rainfall "anomaly", that is how high or low the total for a given year is in relation to the long-term average. The maps show the geographic distribution of rainfall, or lack of rainfall:<p>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/graphrainfall.png)
<br>

<p> We have really high variability in the rainfall and temperature. So, when it does rain, more of that water is likely to be lost to the atmosphere through evaporation than before human-caused climate change.<p><br>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/rainfallmaps1.jpeg)
<br>

<h2><p>5) Machine Learning Models:<p></h2><br>
<h3><p>[1] Baseline Model - Logistic Regression:<p></h3>
<p>We've implemented Logistic regression to explain realtionships between variables wherein Rainfall tomorrow is the dependant binary variable. We've implemented the models with and without consideration of MoonPhase function. We've converted the MoonPhase function to numerical equivalent to learn its effects on rainfall. <p>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm1.png)

<br>	
<h4><p>We’ve calculated Precision, Recall, F1-score, Support, area under the curve, and Accuracy score for the models. For Logistic regression: <p></h4><br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm2.png)

<br>

<h4><p>The model performance: Confusion matrix and feature performance<p></h4><br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm3.png)

<br>
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm4.png)

<br>

<h3><p>[2] Random Forest:<p></h3><br>
<p> The function below shows the values given for different parameters in order to tune the RandomForestClassifier function. The class_weight function where Weights associated with classes in the form {class_label: weight} are provided. If not given, all classes are supposed to have weight one which is the case here. The criterion parameter which is gini by default is changed to entropy here, which is basically the quality of split based on information gain as we are using entropy instead of gini. Maximum depth of tree is 3 nodes. Minimum sample split, minimum sample leaf are kept to their default value. All the parameters makes it easy for us to tweak the model as needed. Mostly the affect is observed the most when we change the number of nodes for the depth. Here the dataset is pretty straight forward and we need not change a lot of parameters from their default value and we have done so. That being said, we have made changes to some of them such as max_depth and criterion as changing them makes substantial difference. With random forest classifier, sometimes the approach taken has to be a trail and error approach where we have to tweak the parameters to get the desired result. Upon running the Random Forest Classifier on our data the result we got an accuracy score of 84% which Is pretty good.</p>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm5.png)

<br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm6.png)

<br>

![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm7.png)

<br>

<h3><p>Comparing the Models:<p></h3><br>
	
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm8.png)
<br>
![alt text](https://github.com/sairam0808/sairam0808.github.io/blob/master/Images/mlm9.png)
<br>
<br>

<h2><p> 6) References:</h2><br>
<br>
[1] Data Source, https://www.kaggle.com/jsphyg/weather-dataset-rattle-package<br>
[2] Genifer Snipes, “Google Data Studio” , https://jlsc-pub.org/articles/abstract/10.7710/2162-3309.2214/<br>
[3] P. Chandrashaker Reddy, A. Suresh Babu, “Survey on weather prediction using big data analytics”,  https://ieeexplore.ieee.org/abstract/document/8117883<br>
[4] ZhanJie Wang , A B M Mazharul Mujib, “The Weather Forecast Using Data Mining Research Based on Cloud Computing”,   https://www.researchgate.net/publication/320795225_The_Weather_Forecast_Using_Data_Mining_Research_Based_on_Cloud_Computing<br>
	
<h2><p> 7) Team Members and duties: <p></h2><br>
	
<p><b>Harshal Sharma:</b> Ran logistic using BigQuery. This was part of a group assignment. It was done by following the steps given in the tutorial for the same.  Framed project flow and helped with deciding the steps required for the project. Prepared dashboards using Google DataStudio.<p><br> 
<p><b>Lavina Sabhnani:</b> Ran models such as logistic regression and random forest on the dataset with Dataflow on google cloud before and after adding new features to the already present dataset. Performed preprocessing on the dataset. Visualized the data and results using python notebook on dataflow.<p><br> 
<p><b>Sairam Rajagopalan:</b> Created and updated the github repository and website. Performed preprocessing on the dataset. Ran logistic using BigQuery. This was part of a group assignment. It was done by following the steps given in the tutorial for the same. Performed exploratory data analysis to determine the important features from the dataset.<p><br>
<p><b>Sonika Kannegalla:</b> Performed changes to the dataset using MoonPhase function. Researched more into the drought aspect of Australian climate. Framed research questions. Ran models such as logistic regression and random forest on the dataset with Dataflow on google cloud before and after adding new features to the already present dataset.<p><br>	

<h2> Thank You! </h2>

