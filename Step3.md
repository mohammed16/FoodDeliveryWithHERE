# Select the Restaurant number 5 in the list for delivery

## Add the following code after ```map.addObject(restGroup);``` within the '}' in the previous step

```javascript
    let deliveryRestPosition = response.items[4].position;
    showRoute(deliveryRestPosition);

```
# Get Route from the selected restaurant to your home with a car

Add the following code before </script> tag

```javascript
        function showRoute(deliveryRestPosition){

            // console.log(restPos);

            let routingParameters = {
                // The routing mode:
                'mode': 'fastest;car',
                // The start point of the route:
                'waypoint0': deliveryRestPosition.lat+','+deliveryRestPosition.lng ,
                // The end point of the route:
                'waypoint1': myPosition.lat+','+myPosition.lng,
                // To retrieve the shape of the route we choose the route representation mode 'display'
                'representation': 'display'
                };

            router.calculateRoute(routingParameters, onResult,
                function(error) {
                    alert(error.message);
            });    
        }
```
[![Foo](/img/s4.png)](/Step4.md) 
