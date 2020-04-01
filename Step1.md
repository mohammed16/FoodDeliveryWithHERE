
Open your favourite IDE or a simple code editor like notepad++
<br>
I use [VSCODE](https://code.visualstudio.com/download)

## Create a file and rename it to 'credentials.js' and save your credentials in it
```javascript

hereAPIKeys = {
    JS_Key :"ENTER_YOUR_JS_APIKEY",
    REST_Key:"ENTER_YOUR_REST_APIKEY"
}

```
## Create a file and rename it to 'index.html' and save the code below in it


``` html
<!DOCTYPE html>
<html>
    <head>
        <title>HERE Logistics Workshop</title>
        <!-- SCRIPTS -->
        <meta name="viewport" charset="UTF-8" content="initial-scale=1.0, width=device-width" />
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-core.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-service.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-ui.js"></script>
        <script type="text/javascript" src="https://js.api.here.com/v3/3.1/mapsjs-mapevents.js"></script>
        <link rel="stylesheet" type="text/css" href="https://js.api.here.com/v3/3.1/mapsjs-ui.css"/>
        <script type="text/javascript" src="credentials.js"></script>
    </head>
    <body>
        <h1 style="text-align: center;">Food Delivery with HERE</h1>
        <div id="mapContainer" style="width: 80vw; height: 50vh; background: #39B6B3; display: block; margin: 0 auto; border: solid 2px black; margin-top: 100px;" > </div>
        <div style="width: 100vw; height: 40px; margin-top: 30px;">
            <input type="button" onclick="showDeliveryRest()" value = "Show Restaurants" style="width: 200px; height: 30px; border: 2px solid black; display: block; margin: 0 auto; margin-top: 20px;">
        </div>
        <div id="panel" style="width: 30vw; background: #39B6B3; color: white; margin-top: 20px;display: block; margin: 0 auto;"></div>
        
    </body>
    <script>
        var platform = new H.service.Platform({
            apikey: window.hereAPIKeys.JS_Key   // JS APIKEY
        });

        // Obtain the default map types from the platform object:

        var defaultLayers = platform.createDefaultLayers();

        // Get your current position from wego.here.com
        
        var myPosition = {lat: 52.53007, lng: 13.38526};

        // Instantiate (and display) a map object:

        var map = new H.Map(
            document.getElementById('mapContainer'),
            defaultLayers.vector.normal.map,
            {
                zoom: 11,
                center: myPosition
            });

        var ui = H.ui.UI.createDefault(map, defaultLayers);

        var mapEvents = new H.mapevents.MapEvents(map);

        var behavior = new H.mapevents.Behavior(mapEvents);

        // Get an instance of the routing service for using the routing API

        var router = platform.getRoutingService();
    </script>
</html>
```

# Adding a position marker using map object of Interactive maps API
Add the following code before </script> tag

```javascript
            // create an icon for the marker. Choose any image you want. I created mine using draw.io 
            
            var homeIcon = new H.map.Icon('img/home.png');
            
            var posMarker = new H.map.Marker(myPosition,{icon:homeIcon});
                
            // Add the marker to the map 

        map.addObject(posMarker);
```
</br> Double-click on saved file to view on browser

[![Foo](/img/s2.png)](/Step2.md) 


