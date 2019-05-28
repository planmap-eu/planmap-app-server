# Meteor

Meteor is responsible for compiling the source code -- HTML, Javascript, CSS --
and deploying the app through a NodeJS package.
The server-side is minimal since data is provided by GeoServer and the client
is responsible for all the data access and rendering.

The server is responsible to communicate specific environment variables to the
client through its public settings.
During development mode, the settings are loaded through `meteor-run` command
and the following `settings.json` file:
```
{
  "public": {
    "geoserver": {
      "url": "https://geoserver.planmap.eu"
    },
    "dataserver": {
      "url": "https://data.planmap.eu/pub/"
    },
    "notebooks": {
      "url": "https://github.com/planmap-eu/planmap-notebooks-code"
    }
  }
}
```
