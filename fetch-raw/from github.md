// 3. Fetch GeoJSON
const geojsonUrl = "INSERT URL";

fetch(geojsonUrl)
  .then(response => response.json())
  .then(data => {

// 4. Add GeoJSON layer
    const geoLayer = L.geoJSON(data, {


    }).addTo(map);

    // 5. Zoom map to GeoJSON bounds
    map.fitBounds(geoLayer.getBounds());

  })
  .catch(err => console.error("Error loading GeoJSON:", err));
