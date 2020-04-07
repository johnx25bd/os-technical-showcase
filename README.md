# Technical Showcase: Outline

## Intro to APIs

- The OS Data Hub, Open MasterMap Implementation Plan and Public Sector Geospatial Agreement
- Why it matters: making it easier and cheaper (free-er) to access OS data
- Goal: to unlock economic value of OS location data

### How They Work

- RESTful APIs using open standards like WMTS, ZXY, VTS, WFS
- Sign up and register for an API key, then send requests from client applications and get data returned

### Session Goals:

- Introduce the OS Maps, Vector Tiles and Features APIs
- Help users understand the capabilities and constraints of each API, and choose which would be right for them
- A technical walkthrough of the key functionality of each API

## The APIs: a quick look

### OS Maps API

- WMTS vs ZXY
- Raster tiles: pros and cons
- OS styles
- Use cases: web mapping in the browser with Leaflet / OpenLayers / Mapbox GL JS (?), basemaps in IPython Notebooks with Folium or R with leaflet, basemaps in GIS applications like ArcMap and QGIS

### OS Vector Tiles API

- WFS
- Vector features returned in GML and GeoJSON
- Examples of layers included
- Rich attribution for analysis or visualisation
- Query API by geometry, attribute, etc
- Transactions return up to 100 features - easy pagination to fetch larger collections of features with multiple requests.
- Use cases: web mapping in the browser with Leaflet / OpenLayers / Mapbox GL JS, analysis in IPython Notebooks with geopandas, visualisation or analysis in GIS applications like ArcMap and QGIS


### OS Features API
- WFS
- Request types
    - GetCapabilities: interpreting the response
    - 
- Feature types
- Parameters
    - key
    - service: 'WFS'
    - request: 'GetFeature',
    - version: '2.0.0',
    - typeNames: feature type name,
    - outputFormat: 'GEOJSON',
    - srsName: 'urn:ogc:def:crs:EPSG::4326',
    - filter: see below,
    - count: 100,
    - startIndex: 0
    - Bounding box
- XML filters ()
    - Spatial filters
    - Filtering by attribute
- Ordering of response 

```xml
<!-- Example 1: Match string match DescriptiveGroup attribute -->
<ogc:Filter>
  <ogc:PropertyIsEqualTo>
    <ogc:PropertyName>DescriptiveGroup</ogc:PropertyName>
    <ogc:Literal>Roadside</ogc:Literal>
  </ogc:PropertyIsEqualTo>
</ogc:Filter>


<!-- Example 2: In bounding box and string match DescriptiveGroup attribute -->
<ogc:Filter>
  <ogc:And>
    <ogc:Within>
      <PropertyName>SHAPE</PropertyName>
      <gml:Box xmlns:gml="http://www.opengis.net/gml" srsName="EPSG:27700">
        <gml:coordinates decimal="." cs="," ts=",">
          436833.50,115334.90,437643.25,115761.50
        </gml:coordinates>
      </gml:Box>
    </ogc:Within>
    <ogc:PropertyIsEqualTo>
      <ogc:PropertyName>DescriptiveGroup</ogc:PropertyName>
      <ogc:Literal>Roadside</ogc:Literal>
    </ogc:PropertyIsEqualTo>
  </ogc:And>
</ogc:Filter>
```

- Constructing a URL

## Fetching Data

### On the terminal with cURL

### From within a JavaScript application

- fetch
- d3.json


### Python
- requests
- urllib2

### ???