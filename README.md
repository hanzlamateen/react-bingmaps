# React-Bingmaps-Plus
## Introduction
React-Bingmaps-Plus is a react.js version of [Bing Maps V8 Web Control](https://msdn.microsoft.com/en-us/library/mt712542.aspx). It is based off of the project React-Bingmaps found here: https://github.com/iniamudhan/react-bingmaps.

This repository was created to add clustering support to React-Bingmaps. The biggest change is that now when you create pushpins or pushpins with infoboxes for the map, they will be added to a clustering layer instead of the map entities list.

**Please note that for the time being, the new clustering features are only available when using the InfoboxesWithPushpins**

The main purpose of this version is to help you to write Bingmaps in React applications without any pain. Main principles of React-Bingmaps are:
1. **Simply** deploy with React components
1. **Lightweight**  depending on Bing Maps V8 Web Control

## Features
* Bingmaps in React.js
* Multiple Pushpin
* Multiple Infobox
* Multiple Pushpin with Infobox
* Callback events in Pushpins and Infoboxes
* Map types
* Disable Street View
* Zoom
* Get Location on Mouse Events
* Regular Polygon
* Boundary
* Polyline
* Directions

## Installation

### npm

NPM is the easiest and fastest way to get started using React-Bingmaps.


```sh
# latest stable
$ npm i react-bingmaps
```

### Import Module
To use react-bingmaps in your react app, you should import it first.

```jsx
import { ReactBingmaps } from 'react-bingmaps';
```

## Examples  
[Click here](https://iniamudhan.github.io/react-bingmaps/)
#### Bingmaps
Follow [Bing Maps Dev Center](https://www.bingmapsportal.com/) to get your Bingmaps key 
```jsx
<ReactBingmaps 
  bingmapKey = "[YourBingMapsKey]" > 
</ReactBingmaps>
```

#### Map center with loaction
```jsx
<ReactBingmaps 
  bingmapKey = "[YourBingMapsKey]" 
  center = {[13.0827, 80.2707]}
  > 
</ReactBingmaps>
```

![Alt text](/src/example/PinPointWithInfobox.png?raw=true "PinPointWithInfobox")

## Other props
##### mapTypeId : string
```jsx
mapTypeId = {"road"}
```
Find more map types - [MapTypeId Enumeration](https://msdn.microsoft.com/en-us/library/mt712700.aspx)

#### navigationBarMode : string
```jsx
navigationBarMode = {"compact"}
```
Find more NavigationBar Mode - [NavigationBarMode Enumeration
](https://msdn.microsoft.com/en-us/library/mt736390.aspx)
#### supportedMapTypes : string[]
```jsx
supportedMapTypes = {["road","canvasDark"]}
```
Find more Supported Map Types Mode - [MapTypeId Enumeration](https://msdn.microsoft.com/en-us/library/mt712700.aspx)

#### heading : oneOfType([ string, number ])  
**Note:** Available only for map mode - **BirdView** 
```jsx
heading = {180}
```
#### zoom : number
```jsx
zoom = {5}
```
#### disableStreetside : bool
```jsx
disableStreetside={true}
```

#### clusterClickCallback : function
This is the callback function for when a cluster of pushpins is clicked. Currently only supported on infoboxesWithPushPins
```jsx
clusterClickCallback={this.callBackFunction}
```

#### pushPins : ArrayOf(objects)
NOTE: This prop has built-in clustering support
```jsx
pushPins = {
            [
              {
                "location":[13.0827, 80.2707], "option":{ color: 'red' }, "addHandler": {"type" : "click", callback: this.callBackMethod }
              },
              {
                ...
              }
            ]
          }
```
Find more **option** values - [Pushpin](https://msdn.microsoft.com/en-us/library/mt712679.aspx)  
addHandler types - ["click", "mousedown", "mouseout", "mouseup", "mouseover"]

#### infoboxes : ArrayOf(objects)
```jsx
infoboxes = {
            [
              {
                "location":[13.0827, 80.2707], "option":{ title: 'Chennai', description: '...' }, "addHandler": {"type" : "click", callback: this.callBackMethod}
              },
              {
                ...
              }
            ]
          }
```
Find more **option** values - [Infobox](https://msdn.microsoft.com/en-us/library/mt750270.aspx)  
addHandler types - ["click", "mouseenter", "mouseleave"]
#### infoboxesWithPushPins : ArrayOf(objects)
NOTE: This prop has built in clustering support
```jsx
infoboxesWithPushPins = {[
            {
              "location":[13.0827, 80.2707], 
              "addHandler":"mouseover", //on mouseover the pushpin, infobox shown
              "infoboxOption": { title: 'Infobox Title', description: 'Infobox' },
              "pushPinOption":{ title: 'Pushpin Title', description: 'Pushpin' },
              "infoboxAddHandler": {"type" : "click", callback: this.callBackMethod },
              "pushPinAddHandler": {"type" : "click", callback: this.callBackMethod }
            },
            {
              ...
            }
          ]
          }
```

#### getLocation : objects
```jsx
getLocation = {
  {addHandler: "click", callback:this.AddPushPinOnClick}
}
```
Callback Method
```jsx
AddPushPinOnClick(location){
  //Outputs latitude and longitude
  ...
}
```


#### regularPolygons : ArrayOf(objects)
```jsx
regularPolygons = {
            [
              {
                "center":[13.0827, 80.2707],
                "radius":5,
                "points":3,
                "option": {fillColor: "green", strokeThickness: 2}
              },
              {
                ...
              }
            ]
```
Find more **option** values - [PolygonOptions](https://msdn.microsoft.com/en-us/library/mt712648.aspx)

#### boundary : object
```jsx
//Static array of locations
boundary = {
              {
                "location":['chennai'],
                "option":{
                  entityType: 'PopulatedPlace'
                },
                "polygonStyle" :{
                  fillColor: 'rgba(161,224,255,0.4)',
                  strokeColor: '#a495b2',
                  strokeThickness: 2
                }
              }
            }

//Search by string
boundary = {
              {
                "search":"India",
                "option":{
                  entityType: 'PopulatedPlace'
                },
                "polygonStyle" :{
                  fillColor: 'rgba(161,224,255,0.4)',
                  strokeColor: '#a495b2',
                  strokeThickness: 2
                }
              }
            }
```
Find more **option** values - [Get Boundary Options](https://msdn.microsoft.com/en-us/library/mt712819.aspx)

## License

[MIT](http://opensource.org/licenses/MIT)

Copyright (c) React-Bingmaps
