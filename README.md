# UFOs_Challenge
Module 11 Challenge assignment

## Overview of the Statistical Analysis
The objective of this assignment was to build a dynamic table that allows users to filter for multiple criteria at the same time. In addition to the date, filters for the city, state, country, and shape of the sighted UFO were added.
### Resources:
- Data Sources: [data.js](https://github.com/banasibb/surfs_up/blob/7ffb5581e784e225a4126853e1fe9df2e37737af/hawaii.sqlite)
- Software: Python, 3.7.6, Microsoft Virtual Studio Code 1.71.1, SQLAlchemy, Jupyter Notebook 2.27.21
### Analysis Components:
As part of the module coursework (completed prior to the challenge assignment), the following tasks were undertaken to explore the provided weather data:
1. Explain the strengths and weaknesses of JavaScript "standard" and JavaScript version ES6+.
2. Describe JavaScript syntax and ideal use cases.
3. Build and deploy JavaScript functions, including built-in functions.
4. Convert JavaScript functions to arrow functions.
5. Build and deploy forEach (JavaScript for loop).
6. Create, populate, and dynamically filter a table using JavaScript and HTML.
## Results
The analysis can be found in the following file: [SurfsUp_Challenge.ipynb](https://github.com/banasibb/surfs_up/blob/79544847a49a8c16ff56379493862b2f54435fce/SurfsUp_Challenge.ipynb)<br />
### Deliverable 1: Summary Statistics for June
Using JavaScript, a new function that saves the element, value, and id of the filter was added. Then, a new function to loop through the dataset and keep only the results that match the search criteria was added. The webpage is updated with the search criteria after pressing "Enter".<br />
<br />The code used to filter on the month of June was as follows: <br />
 ```
june = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date) ==6)
  ```
A .describe() function was used to calculate the mean, minimum, maximum, standard deviation, and percentiles. The results were as follows:<br />
![June_Temps](https://github.com/banasibb/surfs_up/blob/7ffb5581e784e225a4126853e1fe9df2e37737af/Resources/June_Summary_Stats.png)
### Deliverable 2: Summary Statistics for December
The same methods were applied as for Deliverable 1, but using the temperatures for the month of December. The temperatures were then converted to a list, a DataFrame was created from the list, and summary statistics were generated.<br />
<br />The code used to filter on the month of December was as follows: <br />
 ```
dec = session.query(Measurement.date, Measurement.tobs).filter(extract('month',Measurement.date) ==12)
  ```
A .describe() function was used to calculate the mean, minimum, maximum, standard deviation, and percentiles. The results were as follows:<br />
![Dec_Temps](https://github.com/banasibb/surfs_up/blob/7ffb5581e784e225a4126853e1fe9df2e37737af/Resources/Dec_Summary_Stats.png)
### Findings
- There were 1,700 measurements taken for the month of June, compared to 1,517 for the month of December. 
- The mean or average temperature in the month of June over the time period included in the analysis was approximately 74 degrees, compared to 71 degrees in December. 
- The minimum temperature for the month of December (56 degrees) was approximately eight degrees cooler than the minimum temperature in the month of June (64 degrees). 
## Summary
The findings showed that in terms of temperature alone, the months of June and December are not significantly different. The analysis could be improved upon if the precipitation data were incorporated into the analysis, as this may offer more insight into weather fluctuations that could impact sales.
### Additional Query 1: Include Preciptation for the Month of June
The following code was used to create a new DataFrame that includes preciptation data for the month of June: <br />
 ```
juneprcptobs = session.query(Measurement.date, Measurement.prcp, Measurement.tobs).\
filter(extract('month',Measurement.date) ==6).all()
june_tobs_prcp=list((juneprcptobs))
june_tobs_prcp_df = pd.DataFrame(june_tobs_prcp,columns=['date','June Precip','June Temps'])
june_tobs_prcp_df.set_index(june_tobs_prcp_df['date'],inplace=True)
june_tobs_prcp_df.describe()
  ```
The results were as follows:<br />
![June_Rainfall_Temps](https://github.com/banasibb/surfs_up/blob/698ab82178b4b63a6e83a6437ea81a21571ab32a/Resources/June_Summary_Rainfall_Temps.png)
### Additional Query 2: Include Preciptation for the Month of December
The following code was used to create a new DataFrame that includes preciptation data for the month of December: <br />
 ```
decprcptobs = session.query(Measurement.date, Measurement.prcp, Measurement.tobs).\
filter(extract('month',Measurement.date) ==12).all()
dec_tobs_prcp=list((decprcptobs))
dec_tobs_prcp_df = pd.DataFrame(dec_tobs_prcp,columns=['date','Dec Precip','Dec Temps'])
dec_tobs_prcp_df.set_index(dec_tobs_prcp_df['date'],inplace=True)
dec_tobs_prcp_df.describe()
  ```
The results were as follows:<br />
![Dec_Rainfall_Temps](https://github.com/banasibb/surfs_up/blob/caa087ca758b76a02a0931f46d9ed8901bc466af/Resources/Dec_Summary_Rainfall_Temps.png)
