# File-server

The File-server used by Planmap -- https://data.planmap.eu -- is customization
of the Apache2 server by the [Apaxy](https://oupala.github.io/apaxy/) project
with further modifications for Planmap.

For Planmap, a Markdown parser -- the [Showdown] javascript library --
was included to a proper rendering of the
`README.md` files included in each map package.
The customizations used by the project can be found at https://github.com/chbrandt/apaxy/tree/planmap.

Like the project's GeoServer, Planmap's File-server runs in a Docker container,
found at https://cloud.docker.com/u/chbrandt/repository/docker/chbrandt/apaxy.

The File-server publishes data under `/var/www/html`.

[showdown]: https://github.com/showdownjs/showdown
