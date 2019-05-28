# GeoServer

Planmap uses an instance of GeoServer version 2.14.3 dedicated to the project
at the address https://geoserver.planmap.eu.


## Software environment

Planmap's GeoServer runs from inside a Docker container to allow a stable
setup for the development and test of new datasets without compromising the
production service.

To allow the backup of the ingested data metadata GeoServer's `GEOSERVER_DATA_DIR`
is split from the main software directory structure.
For instance, in the Planmap environment, the data settings are stored in
`/var/lib/geoserver_data`.

The Dockerfile used can be found at https://github.com/chbrandt/docker-geoserver.
The Docker container is available at https://cloud.docker.com/repository/docker/chbrandt/geoserver.

In practice, GeoServer sees two data volumes/directories:
* input (or _native_) data -- Planmap's raster/vector maps and global mosaics;
* data base settings and metadata.

The _native_ data is a replica of the data found in Planmap's fileserver,
https://data.planmap.eu/pub; Both data storages are kept separated to avoid
a single point of failure.


## Data

Besides the data produced and published by Planmap -- the _maps_ from specific
regions of the Moon, Mars, and Mercury -- global basemaps are used for visualization
purposes.
The global mosaics are provided by USGS Astrogeology service, https://astrogeology.usgs.gov.
In particular, we the following basemaps were chosen:
* Moon: [LRO LROC-WAC Global Morphology Mosaic 100m June2013](https://astrogeology.usgs.gov/search/map/Moon/LRO/LROC_WAC/Lunar_LRO_LROC-WAC_Mosaic_global_100m_June2013)
* Mars: [MGS MOLA Global Grayscale Hillshade 463m](https://astrogeology.usgs.gov/search/map/Mars/GlobalSurveyor/MOLA/Mars_MGS_MOLA_Shade_global_463m)
* Mercury: [Mercury MESSENGER MDIS Basemap LOI Global Mosaic 166m](https://astrogeology.usgs.gov/search/map/Mercury/Messenger/Global/Mercury_MESSENGER_MDIS_Basemap_LOI_Mosaic_Global_166m)


### Projection

Planmap' maps are ingested and published in their native projection,
global basemaps though are reprojected to `EPSG:4326` before adding them to GeoServer.
The reason is mere visual: the webapp displays data in `latlong`; While GeoServer
is perfectly capable of reprojecting the individual (Planmap) maps on demand, the
convertion of global rasters in realtime are expensive and prone to fault.


### Settings

Planmap data packages are structured in _raster_ and _vector_ files.
The vector data is packaged in a [GeoPackage](https://www.geopackage.org/),
which is a composition of the different features of the corresponding map.
GeoPackage is composed by multiple tables -- or _layers_ --, each one storing
different features.
The number of layers and label used by each map/package is defined by the
respective author, there is one layer that is common to all geopackages:
`layer_styles`, which is the table providing the map' SLD-/QML-format styles.
