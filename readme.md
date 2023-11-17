# Enjoy The Outdoors

This project is a website that starts at the homepage and has two pages

1. The link on the left is the National Park Search page
2. The link on the right is the Mountain Information page
   These pages both have information for the user for what they are searching for.

## Demo for the Homepage, Mountain Page and National Park Search Page

![This Gif shows the demos for each page](https://github.com/tacostrash/CapstoneTwo_EnjoyTheOutdoors/blob/main/Capstone2.gif?raw=true)

## Acknowledgements For The Code I Used

```JS
 // Check to see if the park type is not already included currently
   if (!uniqueParkTypes.includes(parkType)) {

    // if not then add the park type to the uniqueParkTypes and it displays the options for park type

    uniqueParkTypes.push(parkType);
    parkTypeDropdown.innerHTML += `<option value="${parkType.toLowerCase()}">${parkType}</option>`;
  }
```

## Function for search park by location and park type

```JS
//Assigns the searchPark function so when you click it displays one of the following
searchButton.onclick = searchParks;

function searchParks() {
const location = locationDropdown.value;
const parkType = parkTypeDropdown.value.toLowerCase();

//If statement so that you will be required to choose one or the message below will display
if (!location && !parkType){
 resultsBox.innerHTML = "<p> Please select at least one: location or park type.</p> ";

 return;
}

//  Empty Array will store the parks selected
  const results = [];

  //Goes through the each national park but it is now assign to park variable
  for (let i = 0; i < nationalParksArray.length; i++) {
    const park = nationalParksArray[i];

    // checks if the location is empty or if the park's state matches the location it is now in matchesLocation
    const matchesLocation =
      location === "" || park.State.toLowerCase() === location.toLowerCase();

    //This line checks if the park's location name includes the specified parkType. The result is stored in the matchesParkType variable.
    const matchesParkType = park.LocationName.toLowerCase().includes(parkType);

    //This if statement checks if both conditions (matchesLocation and matchesParkType) are true. It is added to the results array using results.push(park).
    if (matchesLocation && matchesParkType) {
      results.push(park);
    }
  }

  // The results of the parks is within the results and also calls displayResults function to show the results
  displayResults(results);
}

```

## Mountain Array Code

```JS

//It gos through each mountain
for(let i=0; i < mountainsArray.length; i++){

 //For each mountain, it creates a new <option> HTML element using document.createElement("option"). This element will be used to create the dropdown.
const mountain = mountainsArray[i];
const option = document.createElement("option");

 //This sets the value and the text of the <option> element to the name of the current mountain.
option.value = mountain.name;
option.text = mountain.name;

//It adds the created <option> element to the <select> dropdown (selectMountainEl).
selectMountainEl.add(option);
}
```

## Finding and Displaying the Mountain 

```JS

// when the user changes the selected option in the dropdown, the code gets the name of the selected mountain from the dropdown's value, and then it gets the mountainsArray for a mountain with that name. The found mountain is stored in the selectedMountain variable, then it displays for that specific mountain


SelectMountainEl.onchange = function(){

  const selectedMountainName = selectMountainEl.value;
  const selectedMountain = mountainsArray.find((mountain)=>mountain.name === selectedMountainName);

   mountainInfoDiv.innerHTML = `<h2>${selectedMountain.name}</h2>
  <p><strong>Elevation:</strong> ${selectedMountain.elevation} feet</p>
  <p><strong>Effort:</strong> ${selectedMountain.effort}</p>
  <img src="${selectedMountain.img}" alt="${selectedMountain.name}" class="img-fluid mb-3">
  <p><strong>Description:</strong> ${selectedMountain.desc}</p>
  <p><strong>Coordinates:</strong> Latitude ${selectedMountain.coords.lat}, Longitude ${selectedMountain.coords.lng}</p>`;
}

```

## Authors

- [@tacostrash](https://www.github.com/tacostrash)
