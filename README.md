# UFOs_Challenge
Module 11 Challenge assignment

## Project Overview
The objective of this module and Challenge assignment was to create a fully dynamic and filterable table using data stored in a JavaScript array and then place the table into an HTML file for easy viewing. The HTML webpage was customized using Bootstrap, and several fully functional filters, including date, city, state, country, and shape of the sighted UFO, were added to allow users to interact with the visualization. 
### Resources:
- Data Sources: [data.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/data.js)
- Software: Microsoft Virtual Studio Code 1.71.1, JavaScript, ECMAScript, Google Chrome 106.0.5249.121 
### Analysis Components:
As part of the module coursework (completed prior to the Challenge assignment), the following tasks were undertaken to explore how JavaScript can be leveraged to create data visualizations:
1. Learn the strengths and weaknesses of JavaScript "standard" and JavaScript version ES6+.
2. Describe JavaScript syntax and ideal use cases.
3. Build and deploy JavaScript functions, including built-in functions.
4. Convert JavaScript functions to arrow functions.
5. Build and deploy forEach (JavaScript for loop).
6. Create, populate, and dynamically filter a table using JavaScript and HTML.

### Deliverable 1: Filter UFO Data Based on Multiple Search Criteria
Using JavaScript, a new function that saves the element, value, and id of the filter were added to allow multiple search criteria. A new function to loop through the dataset and keep only the results that match the search criteria was also added. The result is that the webpage is updated with the search criteria after pressing "Enter".<br />
<br />The modified starter code can be found in the following file: [app.js](https://github.com/banasibb/UFOs_Challenge/blob/8a40c0a7152cc80807abc826261c301a0427dc4e/static/js/app.js)<br />
<br />Excerpt of code for additional filter parameters:
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
<br />The HTML file ([index.html](https://github.com/banasibb/UFOs_Challenge/blob/9e1e3a2e5986da6396f3778e327877c73c2dfa95/index.html)) was updated to include the new filters with the following code: <br />
 ```
                  <!-- Date Filter -->
                  <li class="list-group-item bg-dark">
                  <label for="date">Enter Date</label>
                  <input type="text" placeholder="1/10/2010" id="datetime" />
                  </li><!-- City Filter -->
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
  ```
Here is an excerpt of the webpage:<br />
![excerpt_page](https://github.com/banasibb/UFOs_Challenge/blob/588341bed3f1266264887c8013396da308131160/Resources/excerpted_page.png)
## Results
To search the data, the user must enter a value for at least one search field located on the left, followed by pressing "enter." The data will automatically filter to reflect the results:
![filtered_data](https://github.com/banasibb/UFOs_Challenge/blob/31c9fdafbdf527e69e22dfb1c36e0ab342f66c11/Resources/filtered%20search.png)
## Summary
### Limitations of Webpage
My primary recommendation is to improve the usability of the search fields by making them drop-down menus in place of text fields. This will ensure that the user is selecting the correct acronym for state or country, in addition to informing the user as to what shape options are available. <br />
<br /> By adding the option to search for a range of dates, this might also significantly improve the usability of the page.
### Further Development
The page could be improved upon if it included summary data on the volume of information the end user is able to search. This could be further enhanced if the data could be viewed in separate tabs where it is sorted by city, state, country and other parameters.<br />
<br /> A second opportunity for improvement would be to include a button to export the results to a CSV file, should the user wish to reference the specific output of their search criteria later, without having to recreate the specifications entered in the filter fields. 
