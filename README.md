# Technical Showcase: Outline

## Intro to APIs

## How They Work

## Contructing a Query

### OS Maps API
- WMTS vs ZXY
- 

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