GeoReference - UE4 Plugin
===========================

This plugin provides a reference between game coordinates and geo-coordinates. The core of the concept is the GeoRegion which defines latitude and longitude of the world origin. Additionally a map size in meter is given to calculate border coordinates in WSG84 and UTM. This information can be used to get georeferenced objects to the correct position. GeoCoordinates are internally stored as double precision WGS84 coordinates but can be initialized from and converted to any valid EPSG coded coordinate reference system.

### GeoReferenceActor
Has to be placed in the world to define the GeoReference. Is used by GeoLocatedActors to calculate game-coordinates.

### GeoLocatedActor
Can be used to derive child blueprints which can be placed at a geo-coordinate which is automatically translated to game-coordinates. Needs a GeoReferenceActor placed in the world.

### GeoLocationComponent
Can be added to any Actor to place the actor at geo coordinates. Sets the owning actors world location. Needs a GeoReferenceActor placed in the world.

### GPSComponent
Can be used to get owning Actors world location in geo coordinates. Needs a GeoReferenceActor placed in the world.

## Building

This plugin uses [UnrealGDAL](https://github.com/TensorWorks/UnrealGDAL), [ue4cli](https://github.com/adamrehn/ue4cli) and [conan-ue4cli](https://github.com/adamrehn/conan-ue4cli) to build and manage the required GDAL libraries.

* Download a Release of UnrealGDAL and place it in the Plugins directory or clone and follow instructions to build UnrealGDAL from source.
## Usage

Add GeoReference to `.uproject` or `.uplugin`

```json
"Plugins": [
  {
    "Name": "GeoReference",
    "Enabled": true
  }
]
```

Add build dependencies to your modules

```csharp
PublicDependencyModuleNames.AddRange(
  new string[]
  {
    "GeoReference"
  }
);
```

## Attribution
Contains two functions for UTM Zone calculation originally written by Chuck Gantz which he posted in an answer on the newsgroups sci.geo.geology and sci.geo.satellite-nav in 1998 ([Archived conversation](http://www.gpsy.com/gpsinfo/geotoutm/)).

## Funding
Development of this code was partially funded by the German Federal Ministry of Education and Research (BMBF) under funding reference number 13FH1I01IA.
