# Leaflet Example

[Leaflet](https://leafletjs.com) is an open-source JavaScript library for creating interactive maps. Leaflet itself doesn't provide map data; it's a tool for displaying and interacting with maps.

OpenStreetMap (OSM) is a collaborative project to create a free, editable map of the world. It's a vast database of geographical data contributed by volunteers worldwide. OSM provides the actual map data (roads, buildings, points of interest, etc.).

While Leaflet can work with various tile providers, OSM is commonly used as the default or example tile layer in Leaflet tutorials and documentation. Take a look at Leaflet [FAQ page](https://github.com/Leaflet/Leaflet/blob/main/FAQ.md). Also, there is an extension to Leaflet that contains configurations for various free tile providers: https://leaflet-extras.github.io/leaflet-providers/preview.

> Mapbox provides map services and technology - one of those services, Map tiles, can be used in Leaflet as base maps. Mapbox also develops their own open-source GIS library for the browse called [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/guides). One of the key differences now between them is that Mapbox GL JS uses WebGL whereas Leaflet does not. WebGL, for mapping, is much faster in rendering computationally heavy things. It is widely used for creating maps for web applications and data visualization.

## Tile layers
`https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png` is a tile URL template used to request map tiles from OpenStreetMap.

- `{s}`: A placeholder for the subdomain. OpenStreetMap uses multiple subdomains (a, b, c) to distribute the load. Leaflet automatically replaces this with one of the available subdomains.
- `/{z}/{x}/{y}`: These are placeholders that Leaflet replaces with actual values, which are zoom level, x-coordinate of the tile, y-coordinate of the tile.
- Zoom Level ranges from 0 (entire world) to 18-20 (building level detail). At zoom level 0, the entire world fits in a single tile. At zoom level z, the world is divided into 2^z tiles horizontally and vertically.

Maps are divided into a grid of small images called tiles. This system allows for efficient loading and displaying of large maps. Leaflet only loads the tiles visible in the current viewport, plus some extras for smooth panning. As you move around or zoom, it requests new tiles as needed.
