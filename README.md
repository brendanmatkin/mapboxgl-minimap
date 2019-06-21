# Mapbox GL Minimap Control
ES6 Module fork of [original by aesqe](https://github.com/aesqe/mapboxgl-minimap)

**--- work in progress; overall performance can probably be improved ---**

## How to use it

`npm install mapbox-gl`

```javascript
import mapboxgl from "mapbox-gl"
import MiniMap from "mapboxgl-minimap/mapboxgl-minimap.js"

var map = new mapboxgl.Map({
  container: "map",
  style: "mapbox://styles/mapbox/streets-v8",
  center: [-73.94656812952897, 40.72912351406106],
  zoom: 7
});

map.on("style.load", function () {
  // Possible position values are 'bottom-left', 'bottom-right', 'top-left', 'top-right'
  map.addControl(new Minimap(), 'top-right');
});
```

## With Vue

Using [mapbox-gl-vue](https://www.npmjs.com/package/mapbox-gl-vue)  
(This is in a single file component, with mapboxgl-minimap in [project root]/src/utils folder)

```javascript
import mapboxgl from "mapbox-gl"
import Mapbox from "mapbox-gl-vue"
import MiniMap from "@/utils/mapboxgl-minimap/mapboxgl-minimap.js"

export default {
  components: { Mapbox },
  methods: {
    mapLoaded(map) {
      _map.addControl(new MiniMap({
        center: [-110.7155,55.6665],
        zoom: 10,
        zoomLevels:[],  // disable adaptive zoom
      }), 'bottom-right');
    }
  }
}
```

## Options

```javascript
{
  id: "mapboxgl-minimap",
  width: "320px",
  height: "180px",
  style: "mapbox://styles/mapbox/streets-v8",
  center: [0, 0],
  zoom: 6,

  // should be a function; will be bound to Minimap
  zoomAdjust: null,

  // if parent map zoom >= 18 and minimap zoom >= 14, set minimap zoom to 16
  zoomLevels: [
    [18, 14, 16],
    [16, 12, 14],
    [14, 10, 12],
    [12, 8, 10],
    [10, 6, 8]
  ],

  lineColor: "#08F",
  lineWidth: 1,
  lineOpacity: 1,

  fillColor: "#F80",
  fillOpacity: 0.25,

  dragPan: false,
  scrollZoom: false,
  boxZoom: false,
  dragRotate: false,
  keyboard: false,
  doubleClickZoom: false,
  touchZoomRotate: false
}
```

## Compatibility

The latest version should be compatible with maboxgl 0.54.0
