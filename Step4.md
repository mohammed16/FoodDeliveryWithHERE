
# Select instructions from the route to be displayed

## Add the following code before ''' map.getViewModel().setLookAtData({bounds: routeLine.getBoundingBox()}); '''

```javascript

                let maneuver = route.leg[0].maneuver;
                displayInstructions(maneuver);

```

# Display these instructions in the "panel"

```javascript

        function displayInstructions(maneuver){

            let totalTravelTime = 0;
               
                for(let i=0; i< maneuver.length; i++){

                    totalTravelTime += maneuver[i].travelTime ;

                    instructions = maneuver[i].instruction;
                    // console.log(instructions)
                    document.getElementById("panel").innerHTML+= (i+1) + ') '+instructions +  `<br>`;

                }

            document.getElementById("panel").innerHTML+="Estimated time : " + (totalTravelTime/60) + ' min' ;
        }
```

[![Foo](/img/s5.png)](/Step5.md) 

