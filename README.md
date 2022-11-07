# UFOs_Challenge
Module 11 Challenge assignment

## Project Overview
The objective of this assignment was to build a dynamic table that allows users to filter for multiple criteria at the same time. In addition to the date, filters for the city, state, country, and shape of the sighted UFO were added.
### Resources:
- Data Sources: [data.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/data.js)
- Software: Microsoft Virtual Studio Code 1.71.1, JavaScript, ECMAScript 
### Analysis Components:
As part of the module coursework (completed prior to the challenge assignment), the following tasks were undertaken to filter the data and create the webpage:
1. Explain the strengths and weaknesses of JavaScript "standard" and JavaScript version ES6+.
2. Describe JavaScript syntax and ideal use cases.
3. Build and deploy JavaScript functions, including built-in functions.
4. Convert JavaScript functions to arrow functions.
5. Build and deploy forEach (JavaScript for loop).
6. Create, populate, and dynamically filter a table using JavaScript and HTML.
## Results
The modified starter code can be found in the following file: [app.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/app.js)<br />
### Filter UFO sightings on multiple criteria
Using JavaScript, a new function that saves the element, value, and id of the filter was added. Then, a new function to loop through the dataset and keep only the results that match the search criteria was added. The result should be that the webpage is updated with the search criteria after pressing "Enter".<br />
<br />The code used to establish the new filters in the app.js file was as follows: <br />
 ```
var filters = {}
function updateFilters() {
let filter = d3.select(this);
let filteredValue = filter.property("value");
let filterId = filter.attr("id");
 if (filteredValue) {
  filters[filterId] = filteredValue;
 }
 else {
  delete filters[filterId];
 }
    filterTable();
  }
    let filteredData = tableData;
    Object.entries(filters).forEach(([key, value]) => {
      filteredData = filteredData.filter(row => row[key] === value);
    });

    buildTable(filteredData);
  }
  d3.selectAll("input").on("change", updateFilters);
  buildTable(tableData);
  ```
<br />The HTML file was updated to include the new filters with the following code: <br />
 ```
                  <!-- City Filter -->
                  <li class="list-group-item bg-dark">
                  <label for="city">Enter City</label>
                  <input type="text" id="city" />
                  </li>
                  <!-- State Filter -->
                  <li class="list-group-item bg-dark">
                  <label for="state">Enter State</label>
                  <input type="text" id="state" />
                  </li>
                  <!-- Country Filter -->
                  <li class="list-group-item bg-dark">
                  <label for="country">Enter Country</label>
                  <input type="text" id="country" />
                  </li>
                  <!-- Shape Filter -->
                  <li class="list-group-item bg-dark">
                  <label for="shape">Enter Shape</label>
                  <input type="text" id="shape" />
                  </li>
                </ul>
  ```
The resulting webpage was as follows:<br />
![UFO_challenge](https://github.com/banasibb/UFOs_Challenge/blob/bb45cbf9bd502a46c1ee9efd3aaa2a84bbb6e312/Resources/Screenshot%202022-11-07%20162307.png)

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
