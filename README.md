# Web Map Critique
## City of New Orleans Roadwork Status Map

In this repository, I will critique a web map that (as of March 13, 2019) can be found at https://roadwork.nola.gov/. This map shows the current status of road work projects in New Orleans, Louisiana, as well as projections and timelines for future projects, broken down on a block-by-block level.

### Intro
**Design Objective**

The objective of this map is to provide the people of New Orleans accurate and timely information on the roadway system of their city.

**Basic Functions**

The map shows the city of New Orleans, overlaid with a layer of the roadways. There are three "layers" to toggle between, each corresponding to a different symbology.
- Pavement condition, rated excellent to failiure
- Planned road construction, showing the project type determined by the initial 2015/16 survey of the road system
- Roads under construction now, showing current projects

Clicking on any given segment opens a pop-up that displays a welath of information for that given segment of roadway, including pavement condition, work status and schedule, and the current budget of the project for that segment.

The map includes a seach by address bar.

Navigation is similar to most web maps, with scroll to zoom and click and drag to pan.

**Target Audience**

The target audience for this map is the people of New Orleans, whether currently there or displaced. The city experienced a 29% loss in population following the 2005 hurricane Katrina, so it's important for the population there to have a reliable source of information on the health of their city.

**Creation Date**

I was unable to find a concrete creation date, but I was able to narrow down to the following:
- No older than "summer 2016", which is when the data displayed in the map was delivered to the city.
- No newer than September 12th, 2018, which is the version shown in the main CSS file for the page.

**Authors and Affiliation**

The author publishing the site is the City of New Orleans. The data was provided by Stantec, a national civil engineering consulting firm.
More information on the project can be found here: https://www.theadvocate.com/new_orleans/news/article_fa7f702c-6c9e-11e6-883a-2f736526c660.html

### Architechture and Design
**System architecture**

The map is housed within a series of divs containing the interactive elements surrounding the map and the map itself.
- The map div interacts with the js of the site to hide and show a set of layers for the different roadway features.
- The map supports zoom levels 0 to 20.

**Design and Cartography Critique**

The map is generally effective and easy to read.
- When zoomed out to the whole-city level or further (zoom level 12 and lower), thematic line features merge into an indistiguishable blob.
- Color choice is good and allows roadway features to stand out from the base map.
  - The Planned Road Construction layer does not seem to have a clear meaning to the colors associated with each project type.
- Water features are blue — easy to distiguish
- The city limits are denoted with a white polygon to call that area out from the rest of the basemap, which is a more muted grey.
- Some labeling is provided to give context, but is not too aggressive or busy.
- Labeling changes cleanly with tiling at different zoom levels, road features on the basemap and the thematic layers do not.

**Data Sources**

The data seems to be the same shapefiles available at [the City of New Orleans GIS site](https://portal-nolagis.opendata.arcgis.com/datasets/dept-of-public-works-roadwork-projects?geometry=-90.405%2C29.882%2C-88.658%2C30.09). This data lives in ArcGIS Online as a shapefile.
The back-end js files, housed on city servers, seem to be pulling the data from ArcGIS Online and linking them to the site interactivity features. This is what allows the attributes for a roadway segment to be pulled up and displayed when clicked. I found this by watching the Network tab in the Chrome inspector as a clicked around the map.
For display, both the basemap and the roadway layers are delivered as png tiles, which load as the map is zoomed and panned. Tiles have only been generated within a small distance of the city limits, which you can see as you zoom out.

**Layering**

Basemap: the basemap is an in-house basemap strored on the city GIS servers. It is delivered as png tiles.
Thematic layer: The themtic layers are also stored as tiles in the same place. These include the three roadway status layers described above.
Interactive features: The interactive features are the ESRI shapefile features pulled from the city's ArcGIS Online server and linked to the map frame's js.

**Map Elements**

The map uses no standard map elements other than the legend, which has the option to slide in or out, obscuring the left side of the map. The legend is reative to the currently selected and displayed roadway layer.
Zoom buttons are included as the sole standard web mapping element.

**Responsive Design**

This map did not load properly on an iPhone or on Chrome's mobile device simulator.
It loaded well on a tablet in Chrome's simulator.

**Further Comments**

This map offers a lot in the way of links to other pages on the site, exportable pdfs, and the ability to link to specific map views. This all makes the map and the site a great place to learn about the projects on the table for New Orleans. The information is easy to navigate, catalog, and share.
