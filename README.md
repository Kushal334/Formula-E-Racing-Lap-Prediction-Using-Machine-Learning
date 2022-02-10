## Formula E-Racing Lap Prediction Using Machine Learning<br>
Formula E Racing is the world’s first full electric, international one-seater, street racing championship. Apart from bringing awareness to fighting climate change, it is also creating a technological and sustainable development test bed that helps address mobility and other environmental issues. Furthermore, it is the first global sport with net zero carbon footprint. 
<br><br>
The prediction question that we have tried to answer is if, using historical data, we can predict the number of laps the driver will need to complete the race. <br><br>
The reason why it's important to solve this business case is because once a driver would know how many laps are left in a race, then that would help him better frame his energy optimization strategy.<br><br>
For example, if our model predicts that the number of laps remaining are 30 with low battery, then the racer could choose to drive conservatively and save energy. On the other hand, if our model would predict the number of remaining laps to be 30 with high battery power, then the racer could choose to drive aggressively and expend energy. Either way, if the racer can better manage their battery expenditure, then that would lead to a better strategy at winning the race. 
<br><br>
![Racer Strategy Picture](https://github.com/Aishwarya4823/Formula-E-Racing-Lap-Prediction-Using-Machine-Learning/blob/main/Images/Strategy_image.JPG)
<br>
## Real Time Prediction
Since we are predicting the total number of laps with respect to each match, if implemented, our real-time predictions to the racer would be as follows : 
<br>

![Model Prediction](https://github.com/Aishwarya4823/Formula-E-Racing-Lap-Prediction-Using-Machine-Learning/blob/main/Images/Prediction%20Equation.JPG)

<br>
## Data
The data that we used for this case competition has been provided by Genpact (https://www.genpact.com/). The data is arranged in a hierarchical format as follows :

```bash
├── data 
│   ├── Season 
│   │   ├── Location 
│   │   ├── ├── Friday Practice Stats
│   │   ├── ├── Qualifying Match Stats
│   │   ├── ├── Final Race Stats
```
<br>

Essentially, a few of the features included in the various datasets were as follows:
1) S1, S2 and S3 lap times<br>
2) Driver License number and Driver name<br>
3) Team Number<br>
4) Class<br>
5) Top Speed<br>
6) KPH<br>
7) Pit Time<br>
8) Total Time <br>
9) Total Laps Completed (upto that point in time)<br>
<br>

Few of the weather data features are as follows :<br>
1) Air temperature<br>
2) Track temperature<br>
3) Humidity<br>
4) Pressure<br>
5) Wind Speed<br>


## Feature Engineering

Because most of our data was in a hierarchical format of of files and folders, we took following feature engineering steps to clean and aggregate our data:<br>
1) Concatenation of datasets across all seasons<br>
2) Creation of new columns to unique identify each match with location, season, total lap number, total pit count<br>
3) Aggregation of data (to get latest results for each match) by driver name, match type, group and team<br>
4) Inclusion of summary statistics of variables of KPH, S1, S2 and S3 as individual columns to capture each aspect of these numerical variables and their effect on total lap count for each match<br>
5) Summation of all pit time into total pit time<br>

## Exploratory Data Analysis (EDA)
Since we did not have weather data for the test set, we used weather data majorly in our EDA process. Some interesting insights that we discovered were as follows :<br>
1) Second Day of Double Header Races have faster average speeds<br>
2) We observed a slight reduction in median KPH before the drivers sped up for the final lap<br>
3) We observed an increase in average speed as the track temperature increased. This variation in speed showed against location as well.<br>


## Data Modelling

For this data, we tried the following four models with their accuracies listed as below 

|   Model                |R2 Score|
|------------------------|-------------------|
|K-Nearest Neighbours    |   0.8811          |
|Random Forest           |   0.9698          |
|Elastic Net             |   0.7948          |

<br>
Additionally, we also developed a weighted average ensemble model that used linear regression to calculate the weights of the outputs of each of the above given three models.<br>
<br>
After plotting the output for each of these models, we observed that although Random Forest performed the best out of the individual models, the output of the ensemble model was the closest to the real predictions. This can be observed in the graph below:<br>
<br>

![Models' Outputs](https://github.com/Aishwarya4823/Formula-E-Racing-Lap-Prediction-Using-Machine-Learning/blob/main/Tableau%20Graphs/All_model_comparisons.png)

<br>

## Conclusion and Future Recommendations
There were two key insights that we took away from this project which are as follows :<br>
1) The performance of a racer can definitely be improved with a detailed inclusion of temperature and location while predicting the total number of possible laps in a match<Br>
2) It is possible to accurately predict the remaining laps in real-time for a racer given historical racing data using an ensemble model. This will further help the racer device their energy expenditure strategy more accurately which could increase their chances of improving <br>
 

![Future Recommendations](https://github.com/Aishwarya4823/Formula-E-Racing-Lap-Prediction-Using-Machine-Learning/blob/main/Images/Future_Recommendations.JPG)

 
