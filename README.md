Web-Map
=======

Web Map Beginner
<html>
    <head>
        <title>Bangalore Maps</title>
        
        <style>
            #map {
                width: 99%;
                height: 500px;
            }
        </style>
        <script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>
        <script src="./pin_560001.js"></script>
        <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css" />
    </head>
    
    <body>
        <div id="map"></div>
        
        
        <script type="text/javascript">
            var map = L.map('map').setView([ 12.9539974,77.6309395], 13);
            var mapquestUrl = 'http://{s}.mqcdn.com/tiles/1.0.0/osm/{z}/{x}/{y}.png',
            subDomains = ['otile1','otile2','otile3','otile4'];
            var mapquest = new L.TileLayer(mapquestUrl, {maxZoom: 18, subdomains: subDomains});
            mapquest.addTo(map);
            
            //Makrer - point
            
            var mapicon = L.icon({
                                   iconUrl: 'mapicon.png',
                                   
                                   iconSize:     [50,50] // size of the icon
                                  // shadowSize:   [50, 64],
                                  // iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
                                  // shadowAnchor: [4, 62],  // the same for the shadow
                                  // popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
                                   });
                                
                                   var marker = L.marker([12.9539974,77.6309395], {icon: mapicon}).addTo(map);
                                   
                                   //var marker = L.marker([12.951769,77.665369], {icon: mapicon}).addTo(map);
                                   var geojsonMarkerOptions = {
                                       radius: 50,
                                       fillColor: "#ff7800",
                                       color: "#000",
                                       weight: 1,
                                       opacity: 1,
                                       fillOpacity: 0.2
                                   };
        function showMessage(feature, layer) {
            // does this feature have a property named popupContent?
            if (feature.properties && feature.properties.ADDRESS) {
                var msg ="<h2>The details of the postbox at "+ feature.properties.ADDRESS+"</h2>";
                layer.bindPopup(msg);
            }
        }
        
        L.geoJson(postbox, {
                  pointToLayer: function (feature, latlng) {
                  return L.circleMarker(latlng, geojsonMarkerOptions);
                  },
                  onEachFeature: showMessage
                  }).addTo(map);

            //line - styles
           
            //polygon
           
            //WRD
           
            </script>
        
    </body>
</html>
