# UFOs
## Overview of Project
#### Dana wants to build a webpage and table that will allow her to provide a more in-depth analysis of UFO sightings by allowing users to filter for multiple criteria at the same time. In addition to the date, she wants to add table filters for the city, state, country, and shape.

## Results
#### The following is the code that I used to create more table filters. I added filters for the city, state, country, and shape of the UFO table. 

```// from data.js
const tableData = data;

// get table references
var tbody = d3.select("tbody");

function buildTable(data) {
  // First, clear out any existing data
  tbody.html("");

  // Next, loop through each object in the data
  // and append a row and cells for each value in the row
  data.forEach((dataRow) => {
    // Append a row to the table body
    let row = tbody.append("tr");

    // Loop through each field in the dataRow and add
    // each value as a table cell (td)
    Object.values(dataRow).forEach((val) => {
      let cell = row.append("td");
      cell.text(val);
    });
  });
}

// 1. Create a variable to keep track of all the filters as an object.
var filters = {};

// 3. Use this function to update the filters. 
function updateFilters() {

    // 4a. Save the element that was changed as a variable.
    let inputElement = d3.select(this);
    // 4b. Save the value that was changed as a variable.
    let inputValue = inputElement.property("value");
    // 4c. Save the id of the filter that was changed as a variable.
    let inputID = inputElement.attr("id");
  
    // 5. If a filter value was entered then add that filterId and value
    // to the filters list. Otherwise, clear that filter from the filters object.
    if (inputValue) {
      filters[inputID] = inputValue;
    } else{filters ={};};
  
    // 6. Call function to apply all filters and rebuild the table
    filterTable();
  
  }
  
  // 7. Use this function to filter the table when data is entered.
  function filterTable() {
  
    // 8. Set the filtered data to the tableData.
    let filteredData = tableData;
  
    // 9. Loop through all of the filters and keep any data that
    // matches the filter values
    Object.entries(obj).forEach(([fkey, fval]) =>{
      filteredData = filteredData.filter((row) => row[fkey] === fval)
          

    });  
    
    // 10. Finally, rebuild the table using the filtered data
    buildTable(filteredData); 

  }
  
  // 2. Attach an event to listen for changes to each filter
  d3.selectAll("input").on("change",updateFilters);
  
  // Build the table when the page loads
  buildTable(tableData);
  ```
#### To search for a result you are able to use a table which can be seen below
### Images
![search](https://github.com/allisonorourke-ufGfGy/UFOs/blob/main/images/search.png)
![search 2](https://github.com/allisonorourke-ufGfGy/UFOs/blob/main/images/search%202.png)

## Summary
#### One of the drawbacks of this website is that fact that there is no seperation between the introduction and the search. This makes the web page seem crowded and overwheliming. 
#### I believe that one of the ways that this webpage could be developed further is to create a menu where you could go to different pages to help with the seperation of information.
##### I also believe that this webpage could be made better if there was and other search criteria that would look for specific words within the comment section of the results. This would help to make sure that if someone knows something about the event but not where or when it occured they could look it up with that. 
