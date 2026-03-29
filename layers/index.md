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
// This is where the co-ordinates are read. 
coords = full polygon definition
coords[0] = outer boundary
coords[1] = holes inside the polygon
slice(1) = extract all holes

[Property Layer] - Outer Polygon (orange fill)<br/>
+-------------------------------------------------------+<br/>
// Each of these structures are a separate polygon. Four buildings are mentioned below, but there is a centre quadrant
[Structures Layer] - Blue polygons<br/>        
+----------------+  +-------------+  <br/>
| Structure 1    |  | Structure 2 |  <br/>
+----------------+  +-------------+  <br/>
| Structure 3    |  | Structure 4 | <br/>
+----------------+  +-------------+ <br/>
+---------------------------------------------+ <br/> 

 [Photos Layer] - Markers with Images & Tooltips    <br/>
+-------------------------------------------------------+<br/>
|  Layer Control: Property | Structures | Photographs  |<br/>
+-------------------------------------------------------+<br/>
  L.control.layers(null, {
    "Property": propertyLayer,
    "Structures": structuresLayer,
    "Photographs": photosLayer
  }, { collapsed:false }).addTo(map);
  


+-------------------------------------------------------+<br/>
