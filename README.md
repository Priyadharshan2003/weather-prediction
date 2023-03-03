# THE SHIELD (HEAT WAVES APPROCH NOTE)
# d9d37933-f9cf-4c64-a515-64fae96847a6
https://sonarcloud.io/summary/overall?id=examly-test_d9d37933-f9cf-4c64-a515-64fae96847a6

## We have gathered data from the provided AQI and Heatwave data, which was taken between 2015 and 2021. The model will be trained on the aforementioned data. The test year will be 2022, after which forecasts for 2023 will be made.

## THE WAY WE APPROCH 

Algorithms and Techniques 

We intend to use the following two methods for both questions—heat wave prediction and air quality index.

# 1.A RNN with LSTM and GRU based on the work from research paper
  
The two most sophisticated time series predictors, LSTM and GRU, were combined by the authors of the cited paper to produce results that were superior to those of the methods used separately. Modern algorithms for predicting time series data, like ours, include LSTM and GRU. In order to forecast time series data, we want to combine the strengths of LSTM and GRU.   
 
 ## LSTM:  
Recurrent neural networks (RNNs) of a LSTM (Long Short-Term Memory) variety are frequently employed for processing sequential data. 

## WHY WE USE LSTM:  

1. Handling long-term dependencies: Because LSTMs are made to record long-term dependencies in consecutive data, they are ideal for time series data, where patterns and trends can endure for a very long time.

2. Handling disappearing gradients: When handling lengthy sequences, conventional RNNs frequently experience the vanishing gradient problem. LSTMs are prepared to manage this problem. As a result, LSTMs work well with time series data, where patterns and trends can last for a very long time.

3. Flexibility: LSTMs can manage a broader variety of complex relationships in the data because they have a more complex structure than GRUs. Due to the complexity of the connections between variables and trends in the data, LSTMs are well adapted for time series data.

4.Improved performance: For a variety of time series prediction tasks, LSTMs have been proven to outperform other types of RNNs, including GRUs, making them a popular option for many practitioners.

 Widely utilised: LSTMs have been used and studied extensively for more than 20 years, and a substantial body of research and best practises have been formed around their use, making them an established and well-understood method for handling time series data.
 
 ## GRU:  
 
WHY WE  USE GRUs: 
1. Handling long-term dependencies: GRUs are made to capture long-term dependencies in sequential data, much as LSTM. This makes them a strong fit for time series data, where patterns and trends can endure for a very long time.
2. More effective computation: Compared to LSTMs, GRUs are more effective at processing big time series datasets, which can be computationally demanding.
3. Simple to train: GRUs are simpler to train and less prone to overfitting than LSTMs since they contain fewer parameters.
4. Reliable performance: GRUs have been demonstrated to be effective in a variety of time series prediction applications, such as predicting stock prices, sales, and energy usage. As a result, many practitioners favour using GRUs.
5.Interpretability: When working with time series data, where the interactions between variables and patterns in the data might be complex, GRUs' simpler structure than LSTMs can make them easier to analyse and comprehend.
The model will be created in Python using TensorFlow, and any necessary adjustments will be made to hyperparameters like the number of neurons and dense layers.

## A neural network based on Neural Prophet 
WHY WE USE :
Facebook Prophet was overtaken by NeuralProphet, which became the de facto benchmark for comprehensible, expandable, and user-friendly forecasting frameworks. Explainable forecasting is still a difficult task for commercial and operational decision making given the abundance of time series data. To fill the gap between interpretable classical approaches and scalable deep learning models, hybrid solutions are required.
A hybrid forecasting framework built on PyTorch and taught using common deep learning techniques is called NeuralProphet. Auto-regression and covariate modules, which can be set up as conventional linear regression or as neural networks, introduce local context. Other than that, NeuralProphet maintains Prophet's design ethos and offers the same fundamental model building blocks.
Our findings show that NeuralProphet, when applied to a set of generated time series, generates interpretable forecast components of equal or better quality than Prophet. For a variety of real-world datasets, NeuralProphet outperforms Prophet. NeuralProphet increases forecast accuracy for short- to medium-term forecasts by 55 to 92 percent.

## Heat Wave Forecasting: 
Feature Extraction 
Studying the research on the factors of heat waves highlights a number of variables, as was mentioned previously in the introduction. some of these factors, like humidity, precipitation, and windspeed, are well known locally. However, other, less well known locally, factors, like surface soil moisture and a combination of cloud cover and daylight hours, show promising results when used as components of larger statistical models, like the proposed SEMB model (Soil Energy and Moisture Budget). These elements will be the stimulus for our potent neural networks.

Since the Earth is a continuous system, phenomena occurring in one area, particularly the seas, have a major influence on a station's weather. Thus, as shown by Rohini P. et al. [4], variables like the ONI (Oceanographic Nino Index) play a significant part in deciding the climactic circumstances of a station in any given year. MJO (Madden-Julian Oscillation) amplitude and SST (Surface Sea Temperatures) from the world's main seas (Indian, Pacific, and Atlantic) at different pressure levels will also be taken into consideration, as shown in the work of Guigma K.H. et al. [5].

We intend to use a variety of methods, including but not limited to data scraping with bots, querying open APIs, and reverse engineering open government APIs, to gather data every day for the features listed below.

## Usage
For each of the five areas, we intend to use two different models and the aforementioned methods.
The best model will be picked for each location after the findings are compared. The comparative measures will be the common MAE, MAPE, and R2 score metrics. Data from the first four years will serve as training data, and data from the final year (i.e. 2022) will serve as assessment data.
The forecast from the algorithms will then be saved as a CSV or Parquet file for later use. 

## AQI: 
Different models for time series data for each of the pollutants For time frame 2018 - 2022 
•	PM 2.5  
•	PM 10 
•	NO2 
•	SO2 
•	CO 
•	O3 

Then, as per India AQI rules, the highest scaled pollutant will determine the overall AQI. 

## Features Extracted: 
From literature review of the problem of Air Quality prediction, we decided on the factors for which data should be collected. Again, some were prominent and obvious factors affecting the air quality such as precipitation, number of vehicles and forest cover. This is also backed by relevant studies such as work done by Dongsheng Zhen et.al. [7]. However, there were surprising results in the literature such as the strong positive correlation of Per Capita Income [6] with AQI, i.e., the more the average income of a place, worse is the air quality. According to the work done in the same publication, Construction has been determined as a leading cause for worsening AQI. Thus, SGDP attributed to construction is also chosen as a feature [6]. Another such revelation was that Urbanization Level is not a significant contributor to the Air Quality of a place. Daily temperature is not considered as it is not a causal factor, rather it is an effect of the Air Quality. 

## FEATURE 	DATASET 
Monthly AQI 	Monthly AQI for districts in Telangana (2018-2022) 
Daily precipitation (Cumulative Rainfall) 	
Motor Vehicle Tax collected 	Telangana SEO (Socio-Economic Outlook Report 20182022) [Telangana State Portal Reports] 
(https://www.telangana.gov.in/downloads/reports) 
Construction contribution to GSDP 	
Personal Income per Capita 	
Relative Humidity 	
 
## Usage 
Similar to the Heat Wave models, we create a model for each pollutant for each of the 5 districts. The predicted concentration for each pollutant is then scaled to the AQI indices then choosing the worst pollutant, which is considered to be the prevailing AQI. 
 	 
Libraries to be used: 
•	PyTorch 
•	TensorFlow 
•	Suntime 
•	Python Base packages 
•	Matplotlib 
•	Seaborn 
•	Sklearn 
•	Flask • 	Vue3 

## DATASET 

|     FEATURES                                                           |     DATASET                                                                                                                                                                                   |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     Cumulative Rainfall                                                |     Telangana Daily Weather Data 2018 - 2022([Telangana Weather   Data      2022 \| Telangana Open Data      Portal](https://data.telangana.gov.in/dataset/telangana-weather-data2022))       |
|     Temp Max                                                           |                                                                                                                                                                                               |
|     Humidity Max                                                       |                                                                                                                                                                                               |
|     Humidity Min                                                       |                                                                                                                                                                                               |
|     Wind Speed Max                                                     |                                                                                                                                                                                               |
|     Wind Speed Min                                                     |                                                                                                                                                                                               |
|     Cloud Cover                                                        |     National Information System for Climate and Environmental   Studies      (Satellite Data from various satellites such as CARTOSAT   and INSAT)                                            |
|     Surface soil moisture                                              |                                                                                                                                                                                               |
|     Daylight Hours (Number of hours between sunrise and   sunset)      |     Using python library suntime                                                                                                                                                              |
|     ONI (Oceanographic Nino Index)                                     |     NOAA   Oceanic Nino Index (ONI) [Climate Prediction Center - ONI (noaa.gov)]                                                                                                              |
|     MJO amplitude (RMM1 +      RMM2)                                   |     NOAA MJO Index Data 1971-2022      [NOAA][https://www.psl.noaa.gov/mjo/mjoindex/]                                                                                                         |
|     SST Tropical Pacific at various pressure levels                    |     [International   Comprehensive Ocean-Atmosphere Data Set      (ICOADS)][(https://icoads.noaa.gov/products.html)]                                                                          |
|     SST Tropical Atlantic at various pressure levels                   |                                                                                                                                                                                               |
|     SST Indian Ocean at various pressure levels                        |                                                                                                                                                                                               |

The data will be cleansed after it has been gathered. Encoding is not necessary because we have not examined categorical data; however, each datapoint will be scaled using standard scaling using sklearn's StandardScaler.
