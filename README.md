# UFOs_Challenge
Module 11 Challenge assignment

## Project Overview
The objective of this assignment was to build a dynamic table that allows users to filter for multiple criteria at the same time. In addition to the date, filters for the city, state, country, and shape of the sighted UFO were added.
### Resources:
- Data Sources: [data.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/data.js)
- Software: Microsoft Virtual Studio Code 1.71.1, JavaScript, ECMAScript 
### Analysis Components:
Using JavaScript, a new function that saves the element, value, and id of the filter was added. Then, a new function to loop through the dataset and keep only the results that match the search criteria was added. The result is that the webpage is updated with the search criteria after pressing "Enter".<br />
<br />The modified starter code can be found in the following file: [app.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/app.js)<br />
### Filter UFO sightings on multiple criteria
The code used to establish the new filters in the app.js file was as follows: <br />
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

## Results
There is a description of how to perform a search, with images. (4 pt)
 The resulting webpage was as follows:<br />
![UFO_challenge](https://github.com/banasibb/UFOs_Challenge/blob/bb45cbf9bd502a46c1ee9efd3aaa2a84bbb6e312/Resources/Screenshot%202022-11-07%20162307.png)
To search the data, the user must enter a value for at least one search field located on the left, followed by pressing "enter." The data will automatically filter to reflect the results:
![filtered_data](https://github.com/banasibb/UFOs_Challenge/blob/31c9fdafbdf527e69e22dfb1c36e0ab342f66c11/Resources/filtered%20search.png)
## Summary:

The summary addresses one drawback of this webpage (2 pt)
The summary addresses two additional recommendations for further development (4 pt)


