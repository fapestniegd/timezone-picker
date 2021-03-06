Live demo: http://scratch.andrewl.in/timezone-picker/example.html

Prerequisites
-------------
  - jQuery
  - Google Maps Javascript API v3

Usage
-----
See example.html

    tar xvf tz_json
    python -m SimpleHTTPServer
    http://localhost:8000/example.html

Setup
-----
To use in your site, extract tz_json.tgz to a web-accessible location on your
server and pass in the path as the jsonRootUrl option

Options
-------
  - fillColor: the color of the fill of the rendered timezones (default '#ffcccc')
  - fillOpacity: the opacity of the outline of rendered timezones (default 0.5)
  - initialLat: the initial latitude for the center point of the map (default 0)
  - initialLng: the initial longitude for the center point of the map (default 0)
  - initialZoom: the initial zoom level of the map (1-20, default to 2, 1 is most zoomed out)
  - jsonRootUrl: the default root URL for the JSON data files (default '/tz_json/')
  - strokeColor: the color of the outline of rendered timezones (default '#ff0000')
  - strokeWeight: the width of the outline of rendered timezones (default 2)
  - strokeOpacity: the opacity of the outline of rendered timezones (default 0.7)
  - onHover: callback when a timezone is hovered.  Parameters: utcOffset (in minutes), tzNames (array of strings)
  - onReady: callback when all the data files are loaded
  - onSelected: callback when a timezone is selected via the infowindow. Parameters: olsonName, utcOffset (in minutes), tzName (eg. EST, GMT)

Methods
-------
  - showInfoWindow(htmlString): show an infoWindow for the current selected region.  Takes an HTML string as a parameter
  - hideInfoWindow(): hide it
  - setDate(Date): set the "relative" date for the picker for proper timezone names (eg. EST vs EDT)
  - selectZone(olsonName): programmatically select a timezone

CSS Classes
-----------
  - timezone-picker-infowindow: the main content container for the infowindow

For Data File Generation
------------------------
This plugin uses a bunch of timezone data files on a web server.

  - bounding_boxes.json: an array of bounding boxes for each timezone (for hit testing)
  - hover_regions.json: an array of polygons representing hover regions for each timezone
  - polygons/*.json: polygon definitions for each timezone

Requires Python 2.6+
Requires libgeos-dev (sudo apt-get install libgeos-dev)
Requires shapely (sudo pip install shapely)
Requires pytz (sudo pip install pytz)

To Generate all timezone data JSON files

  - Download and extract the tz_world file from http://efele.net/maps/tz/world/tz_world.zip
  - python script/gen_json.py <path-to-tz_world.shp> <output-dir>
  - Be very patient...

Acknowledgments
----------------
  - Thanks to Eric Muller for creating the timezone shape files (http://efele.net/maps/tz/world)
  - Thanks to Zachary Forest Johnson for the shp file loading python scripts (http://indiemaps.com/blog/2008/03/easy-shapefile-loading-in-python/)