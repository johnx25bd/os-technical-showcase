# Technical Showcase: Outline


## Intro

- Me: John Hoopes, Developer Advocate at Ordnance Survey. 
- Masters in Spatial Data Science and Visualisation at the Bartlett Centre for Advanced Spatial Analysis at UCL.
- Background working in tech startups, civil society organizations and the public sector.

Agenda


## Ordnance Survey in 2020

- OS has a rich history, serving as Britain's national mapping agency since William Roy surveyed Scotland in the mid 1700s.
- As mapping has evolved, so has Ordnance Survey. 
- In 2020, teams of OS surveyors capture high resolution location data about Britain. 
- This is analyzed, parsed, tagged, and stored in a spatial database with 500million features, the OS MasterMap Topography layer. 
- We're constantly innovating, working to provide state of the art location data and map visualization techniques. 
- OS adapts to the needs of the moment. We recently announced our COVID19 license, which makes OS data free for anyone supporting the UK response to the coronavirus pandemic.

## PSGA

- Public Sector Geospatial Agreement => designed to unlock the economic value of Ordnance Survey data by making it easier and less expensive to access and use OS data.
- Read slides
- Today we are going to look at the OS Data Hub, a cornerstone of Ordnance Survey's effort to fulfill our commitment to make it easier for developers, data scientists and other users to access OS data.

## OS Data Hub

- Portal to the new APIs.
- Show demo
- looking at the dashboard, 
- creating a new project and 
- getting a key
- Pricing and licensing
  - Open data
  - Premium data - threshold
  - Reasons for the changes

- Manage account and API keys, monitor usage, access documentation, support and pricing information, and so on. 

## Intro to APIs

- First, what is an API?

- The OS Data Hub, which will include 7 APIs. This webinar will touch on 4 beta services that are live now:
  - OS Maps API
  - OS Vector Tiles API
  - OS Features API
  - Other APIs
  - OS Downloads API

Demo






### How They Work

- RESTful APIs based on Open Geospatial Consortium (OGC) standards.
- OS Maps API => WMTS (ZXY in development)
- OS Vector Tiles API => VTS
- OS Features API => WFS
- Sign up on the OS Data Hub and register for an API key, then send requests from client applications and get data returned

### Session Goals:

- Introduce the OS Maps, Vector Tiles and Features APIs
- Help users understand the capabilities and constraints of each API, and choose which would be right for them
- A technical walkthrough of the key functionality of each API



## The APIs: a quick look

### OS Downloads API

- Enables automated downloads of Ordnance Survey open datasets
- No key needed!
- Can fetch with Node with axios or fetch, curl on the command line, python urllib module, and even in your browser.
- Look at the documentation

### OS Maps API

- WMTS
- Raster tiles: pros and cons
  - Pros: easy, quick, well supported, OS styles out of the box, pretty low bandwidth.
- OS styles
- Use cases: web mapping in the browser with Leaflet / OpenLayers / Mapbox GL JS (?), basemaps in IPython Notebooks with Folium or R with leaflet, basemaps in GIS applications including QGIS

#### Technical Functionality

(with leaflet)
- How a raster tile service works
- Connecting with WMTS
- Specifying style
- Premium zoom levels

[`Demo`](https://observablehq.com/d/8a82bac85a35b05d)

And show png tiles in each style

### OS Vector Tiles API

- VTS
- Vector tiles returned in pbf
  - Why no TileJSON? Is it coming?
- Advantages of vector tiles
  - Smooth zooming
  - Very low bandwidth requirements
  - Customisable layers and styling
  - tilt, extrusion and other 3d effects are available
- Disadvantages
  - Little attribution data with vector features
  - Somewhat expensive for the client to render
- Examples of layers included (Maputnik)
- API dynamically serves tiles by Z, X and Y
- Premium zoom levels?  
- Use cases: web mapping in the browser with Leaflet / OpenLayers / Mapbox GL JS

#### Technical Functionality

1. Connect to the API with Mapbox GL JS
2. Customize layer style with JavaScript
3. Look at customizing map style with Maputnik

(with Mapbox GL JS)
- VTS
- Service metadata endpoint: interpretation
- Style endpoint: interpretation
  - Layers with styles specified
  - Customising vector tile layer styles
  - Forthcoming OS vector tile styles
- Tile Request endpoint: interpretation
  - .pbf files. "Protocolbuffer Binary Format"
  - Vector layers return within tiles
  - Spatial Reference Systems
- Building custom vector tiles styles using **Maputnik**

`Demo`




### OS Features API

- WFS
- Vector features returned in GML or GeoJSON
- Feature vector geometries
- Rich attribution for analysis or visualisation
- Query API by geometry, attribute, etc
- Transactions return up to 100 features - easy pagination to fetch larger collections of features with multiple requests.
- Use cases: web mapping in the browser with Leaflet / OpenLayers / Mapbox GL JS, analysis in IPython Notebooks with geopandas, visualisation or analysis in GIS applications including QGIS

#### Technical Functionality

- The OGC WFS standard
- Request types
    - GetCapabilities: interpreting the response
- DescribeFeatureType
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
- Percent encoding
- XML filters ()
  - Spatial filters
  - Filtering by attribute
- Fetching results 
- Ordering of response 
- Parsing: GeoJSON
- A quick look at GML

`Demo`

## Conclusion

- OS Data Hub APIs