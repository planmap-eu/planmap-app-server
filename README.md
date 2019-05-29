# Planmap - Server

[Planmap web (mapping) app](https://github.com/planmap-eu/planmap-app-client) is supported by three server-side services:
* <a href="./geoserver.md">GeoServer</a>
* <a href="./fileserver.md">Apache File-server</a>
* <a href="./meteor.md">Meteor/NodeJS</a>

GeoServer is responsible for providing the geological maps -- raster and vector data -- live to the app.
GeoServer provides WMS, WFS services used by the client to display the maps on-demand, publishing multi-resolution and location-based data, styles, and custom projections.

Apache File-server provides the "raw" data packages for the users to browse and download.
The interface published was customized to provide a better user experience, allowing the users direct access to the data and metadata describing in fine details the packages contents.

Meteor is the javascript framework that handles the deployment of the web app.
It runs on top of NodeJS and manages the software dependencies and assembly of
HTML and Javascript in a working package.

Support projects:
<div>
<a href='http://geoserver.org/'>
  <img width='100px' src='assets/logo_geoserver.png' />
</a>
<img width='10px' src='assets/slider-transparent-placeholder.png' />
<a href='https://www.meteor.com'>
  <img width='80px' src='assets/logo_meteor.png' />
</a>
<img width='10px' src='assets/slider-transparent-placeholder.png' />
<a href='https://httpd.apache.org/'>
  <img width='80px' src='assets/logo_apache.png' />
</a>
<img width='10px' src='assets/slider-transparent-placeholder.png' />
<a href='https://www.docker.com/'>
  <img width='60px' src='assets/logo_docker.png' />
</a>
</div>
