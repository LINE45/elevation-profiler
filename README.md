# Elevation-Profiler
Elevation-profiler is a Javascript utility for generating an elevation profile from a GeoJSON LineString.

Elevation-profiler relies on Mapbox Terrain-RGB tiles, so a Mapbox API access token is required.

## Installation

With npm:

    npm install @line45/elevation-profiler

## Usage

    import getLineStringElevationPoints from "@line45/elevation-profiler";

    getLineStringElevationPoints(linestring, numberOfPoints, mapboxAccessToken).then(function(featureCollection) {
        // Your featureCollection processing code
    }

### Parameters
    
{Object} lineString: The GeoJSON LineString feature to be checked.

{number} numberOfPoints: The maximum number of points to check along the LineString.

{string} mapboxAccessToken: The mapbox access token to be used to retrieve rgb elevation tiles.

{number} minMetersBetweenPoints (Optional): The minimum distance in meters to use between each point on the LineString. 
                                            By default, the approximate pixel distance at the used zoom level and 
                                            is calculated and used as the minimum distance. Passing null results in 
                                            no minimum being applied, so numberOfPoints points are checked regardless 
                                            of LineString length.

### Return value

The returned GeoJSON FeatureCollection contains all checked points along the provided LineString, with an
"elevation" property attribute containing the point's elevation.