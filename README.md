# Develop interactive maps

Watch the video [FREE maps for any app](https://www.youtube.com/watch?v=UAQogFwyna0):
1. Browser load JS library to display map.
2. Tiles or vectors are requested by JS library based on what part of the map the user is viewing.
3. Tiles are rendered onto the page as images or vectors are drawn to a canvas.
4. Repeat step 2 and 3 as the user zooms/pans around the map.

## Leaflet
[Leaflet](https://leafletjs.com) is an open-source JavaScript library for creating interactive maps. Leaflet itself doesn't provide map data; it's a tool for displaying and interacting with maps.

OpenStreetMap (OSM) is a collaborative project to create a free, editable map of the world. It's a vast database of geographical data contributed by volunteers worldwide. OSM provides the actual map data (roads, buildings, points of interest, etc.).

While Leaflet can work with various tile providers, OSM is commonly used as the default or example tile layer in Leaflet tutorials and documentation. Take a look at Leaflet [FAQ page](https://github.com/Leaflet/Leaflet/blob/main/FAQ.md). Also, there is an extension to Leaflet that contains configurations for various free tile providers: https://leaflet-extras.github.io/leaflet-providers/preview.

### Tile layers
`https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png` is a tile URL template used to request map tiles from OpenStreetMap.

- `{s}`: A placeholder for the subdomain. OpenStreetMap uses multiple subdomains (a, b, c) to distribute the load. Leaflet automatically replaces this with one of the available subdomains.
- `/{z}/{x}/{y}`: These are placeholders that Leaflet replaces with actual values, which are zoom level, x-coordinate of the tile, y-coordinate of the tile.
- Zoom Level ranges from 0 (entire world) to 18-20 (building level detail). At zoom level 0, the entire world fits in a single tile. At zoom level z, the world is divided into 2^z tiles horizontally and vertically.

Maps are divided into a grid of small images called tiles. This system allows for efficient loading and displaying of large maps. Leaflet only loads the tiles visible in the current viewport, plus some extras for smooth panning. As you move around or zoom, it requests new tiles as needed.

- Raster tiles: https://wiki.openstreetmap.org/wiki/Raster_tile_providers
- Vector tiles: https://wiki.openstreetmap.org/wiki/Vector_tiles

## OpenLayers
Alternatively to Leaflet, [OpenLayers](https://openlayers.org) is an open-source JavaScript library for creating interactive maps on web pages. It can display map tiles, vector data and markers loaded from any source. OpenLayers provides more advanced map controls, such as support for vector layers and advanced styling options. OpenLayers also provides support for 3D maps and it’s often used in more complex GIS applications.

## Mapbox GL JS
Mapbox provides map services and technology - one of those services, Map tiles, can be used in Leaflet as base maps. Mapbox also develops their own open-source GIS library for the browse called [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/guides). One of the key differences now between them is that Mapbox GL JS uses WebGL whereas Leaflet does not. WebGL, for mapping, is much faster in rendering computationally heavy things. It is widely used for creating maps for web applications and data visualization.

## The relationship between them
There's a lot of Map things and it's very unclear how they all fit together without prior experience.

- OpenStreetMap (OSM) is a community-driven, fully open and usable data library. It's a database of everything you need to make map.

- OpenFreeMap lets you display custom maps on your website and apps for free *(It provides a vector tile API with an OpenMapTiles schema for free.)* The map data comes from OpenStreetMap. Attribution is required. If you are using MapLibre, they are automatically added, you have nothing to do. https://openfreemap.org

- Mapbox is one of the first companies to take OSM's dataset and commercialize it. Along the way they created a lot of the wildly used mapping libraries, including renders, data formats, and styling tools. Mapbox GL is a completely new implementation of a mapping library written in WebGL (should perform better).

- MapLibre GL JS is a TypeScript library that uses WebGL to render interactive maps from vector tiles in a browser. It originated as an open-source fork of mapbox-gl-js. The library's initial versions were intended to be a drop-in replacement for the Mapbox’s OSS version. MapLibre, stands as an abbreviation for **Map lib**rary **re**started (or **re**invented). https://www.maptiler.com/news/2021/01/maplibre-mapbox-gl-open-source-fork/

- OpenLayers and Leaflet are both alternative, open source renderers with various levels of capabilities.
