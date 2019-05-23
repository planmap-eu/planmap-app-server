# planmap-app-server

[Planmap web (mapping) app](https://github.com/planmap-eu/planmap-app-client) is supported by three server-side services:
* GeoServer
* Apache File-server
* Meteor

GeoServer is responsible for providing the geological maps -- raster and vector data -- live to the app.
GeoServer provides WMS, WFS services used by the client to display the maps on-demand, publishing multi-resolution and location-based data, styles, and custom projections.

Apache File-server provides the "raw" data packages for the users to browse and download. 
The interface published was customized to provide a better user experience, allowing the users direct access to the data and metadata describing in fine details the packages contents.

Meteor is the javascript framework that effectively publishes the app.
It runs on top of NodeJS and manages the software dependencies as well as the orchestration of the app's source code and deploying.
