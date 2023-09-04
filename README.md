# wkt 
This package lets you:
- Parse WKT ([Well-known text](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry)) 
into GeoJSON
- Stringify [GeoJSON](https://geojson.org/) into WKT
## Install
npm install kv-wkt
## Usage

### Parse
Turn [Well-known text](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry) string into GeoJSON

```javascript
const { parse } = require('kv-wkt');

//  See return values in output section
const point_wkt = "POINT (30 10)";
const point_z_wkt = "POINT Z (30 10 10)";
const linestring_wkt = "LINESTRING (30 10, 10 30, 40 40)";
const polygon_wkt = "POLYGON ((30 10, 40 40, 20 40, 10 20, 30 10))";
parse(point_wkt);
parse(point_z_wkt);
parse(linestring_wkt);
parse(polygon_wkt);
```
#### Output from `parse()`
```
{ type: 'Point', coordinates: [30, 10] }
{ type: 'Point', coordinates: [30, 10, 10] }
{ type: 'LineString', coordinates: [ [ 30, 10 ], [ 10, 30 ], [ 40, 40 ] ] }
{ type: 'Polygon', coordinates: [[[30,10], [40,40], [20,40], [10,20], [30,10]]] }
```
### Stringify
Turn [GeoJSON](https://geojson.org/) `geometry` object or Feature object into WKT (Well-known text)

```javascript
const { stringify } = require('kv-wkt');

const geometry = {
  type: "Point",
  coordinates: [30, 10, 10]
};
const geometry2 = { 
  type: "LineString",
  coordinates: [ [ 30, 10 ], [ 10, 30 ], [ 40, 40 ] ] 
};

//  See return values in output section
stringify(geometry);
stringify(geometry2);
```
#### Output from `stringify()`
```
"POINT Z (30 10 10)"
"LINESTRING (30 10, 10 30, 40 40)"
```

