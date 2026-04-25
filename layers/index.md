# Building your own leaflet map (in layers)
//The Document Object Model (DOM) event fires when the HTML document has been completely parsed<br/>

`document.addEventListener("DOMContentLoaded", function () {`
<br/>
+-------------------------------------------------------+<br/>
// We set lattitude, longitude and initialize the leaflet map

`var latit = 48.8336;` 
`var longit = 2.3758;`
`const map = L.map('map', {`
  `doubleClickZoom: false`
`}).setView([latit, longit], 16); `
<br/>

+-------------------------------------------------------+<br/>
// Tiles are called and attribution given. Not too sure why there are some letters in curly braces?

  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors | Wikimedians',
    maxZoom: 19
  }).addTo(map);

+-------------------------------------------------------+<br/>
// This is where the co-ordinates are fetched from github. 
// 3. Fetch GeoJSON
const geojsonUrl = "https://raw.githubusercontent.com/Web-learning/geojson/refs/heads/main/artsfestivals/southafrica.geojson";

fetch(geojsonUrl)
  .then(response => response.json())
  .then(data => {
+---------------------------------------------+ <br/> 

 [GEOJSON Layer] - Markers     <br/>
+-------------------------------------------------------+<br/>
  // 4. Add GeoJSON layer
    const geoLayer = L.geoJSON(data, {


    }).addTo(map);

    // 5. Zoom map to GeoJSON bounds
    map.fitBounds(geoLayer.getBounds());

  })
  .catch(err => console.error("Error loading GeoJSON:", err));
