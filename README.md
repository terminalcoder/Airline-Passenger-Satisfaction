![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/airplane_seats.png.png)
# Airline-Passenger-Satisfaction
Elimelech Berlin  
October 2023
***
## Overview
This report analyzes records of airline customers to construct a classification model to identify customers who are likely to be not satisfied by their experience.
Several different modeling techniques are implemented:
* Logistic Regression
* Random Forest Classifier
* CatBoost Classifier
* Voting Classifier

Ultimately, a random forest classifier is identified as the most performant model. A closer examination of that model reveals what specific factors are most associated with customer satisfaction:
* Online boarding
* Inflight wifi service
* Type of travel

By further examining these features, deeper insight into customer satisfaction is attained.

***
## Business Context
A satisfied customer is a repeat customer.  
A model capable of accurately predicting a customer's dissatisfaction can prove invaluable in equipping an airline with the necesarry insight to modify the elements of service contributing to that dissatisfaction.  
Additionally, the knowledge of which customers will likely be dissatisfied, will provide the airline with a strong basis to preemptively target whoever is predicted to be dissatisfied, thus minimizing overall customer dissatisfaction.

***
## Data
### Data Access
To access the data used for this report & replicate this project on a local machine, follow these steps:
1. Clone this repository to your local machine.
2. Navigate to the dataset on Kaggle [Airline Passenger Satisfaction](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction?rvi=1).
3. Select  `Download` from the top of the page. This will save a folder, archive.zip, to wherever downloads are saved by default on your machine. (You need a Kaggle account to download this file.)
4. Locate the archive.zip file & move it to the `data' file in this directory. (The code is written to handle the zipped file without further manual unzipping or naming of files).


The data used in this report is from the Kaggle [Airline Passenger Satisfaction](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction?rvi=1) dataset. It contains records from an airline passenger survey with ~130k participants. Most of the features of this dataset describe subjective customer ratings of various elements of their experience (e.g. departure/arrival time convenient, cleanliness, inflight wifi), while a few features included describe certain objective elements of flight experiences (e.g. customer age, flight distance, passenger gender).
The target feature is `'satisfaction'`, while all of the other features present in the dataset are the predictor features.

### Feature Distribution
#### Predictor Variables
The predictor features are present in the data with the following distributions:
![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/pred_feat_hist.png)

#### Target Variable
The target variable, `'satisfaction'`, is present in the data with the following distribution:
![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/target_feat_dist_bar.png)
***
## Preprocessing
Several steps were implemented prior to the construction of any models:
- Removal of irrevelant columns
- Impute missing values with column mean
- Transform non-numeric data into numeric type
- Scale the data
## Modeling
Several different modeling techniques are used to identify a classification model which best predicts customer satisfaction:
- Dummy Classifier (baseline)
- Logistic Regression
- Random Forest
- CatBoost
- Voting Classifier
  
Each model's performance is assesed by its recall score on test predictions, for class 0 (neutral or dissatisfied). This is the best metric to use to assess the models' ability to identify every customer who will not be satisfied.
A random forest classifier, with a recall score of .97, is ultimately identified as the best performing model for the data. Its performance is shown: ![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/rfc_conf_matrix.png))
***
## Features
The model reveales which features are most influential to its predictions :
![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/frfc_feat_imp_bar.png)
***
## Conclusions/ Recommendations
### Online Boarding
![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/sat_by_olboarding_bar.png)
* Customers who rated the online boarding experience highly (4 or 5), are far more likely to be overall satisfied by their experience.
> By investing in the development of a streamlined & intuitive interface, the airline will be able to boost customer satisfaction levels.
___

### Wifi Service
![image](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/sat_by_wifi_bar.png)
* With high satisfaction rates amongst customers who rated the inflight wifi service highly (4 or 5), this is a good indicator to the importance of this amenity to overall satisfaction.
> The airline must invest in reliable, fast, & affordable inflight wifi service.
___

### Travel Type
![images](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/sat_by_taveltype_bar.png)
* Customers traveling for business purposes tend to be satisfied with the overall experience in far greater numbers than those that travel for personal reasons. While the reason for this is not obvious, consider the following plot:
![images](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/master/images/travel_type_by_class_bar.png)
* Business travelers tend to fly in business class in far greater numbers than do those who travel for personal reasons. This may result in business travelers having overall greater satisfaction in their experience.
> All levels of travel class must offer more amenities & service that are typically reserved for business class service. 

## Limitations / Next Steps
Th following points should be taken into consideration:

* Much of the information in the dataset used, consists of ratings for a variety of elements of the customer experience. This kind of information is limited in the level of insight it provides in understanding the true motivation of customer dissatisfaction. Data consisting of text-based reviews would provide a more accurate depiction of customer feelings. Further research can be done to obtain such information.
* Additional tuning of model hyperparameters may yield a better result.
* The business case for which this report was compiled dictates that recall for the negative class (neutral or dissatisfied), be the metric by which the models are evaluated. A different business context may demand a different metric.
***
### For More Information
Please review the full analysis in the [Jupyter Notebook](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/main/notebook.ipynb) or the [presentation](https://github.com/terminalcoder/Airline-Passenger-Satisfaction/blob/main/presentation.pdf).  
For any additional questions, please contact Elimelech Berlin, melech.berlin@gmail.com.

***
## Repository Structure
```
├── README.md                                 <- the top-level README for reviewers of this project
├── notebook.ipynb                            <- narrative documentation of analysis in Jupyter notebook
├── presentation.pdf                          <- PDF version of project presentation
├── data                                      <- empty folder in which to store data (see instructions above)
├── .gitignore                                <- files to ignore
├── images                                    <- sourced externally & from code
└── environment.yml                           <- file with environment requirements for jupyter notebook
```

