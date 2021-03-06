## Synopsis

This plugin provides an easy way to distribute and show your QGIS work as a Leaflet webmap. 

## Usage

Your current QGIS project holds different data: vector, raster and plugin layers. QGIS2leaf exports the vector layer to GeoJSON and creates a basic webmap from it with the current Leaflet version 0.7.3. Additionally we add your raster data as image overlays with a opacity slider.

You can choose between several basemap styles and define the initial extent of the map as well as the dimensions of the webmap in your HTML document. To support big data exports you may disable initial loading of the layers to the map. As the webmap has a layer control you can enable visibility of the layers afterwards.

The popup for features is either a simple table with all your attributes or defined by the attribute 'html_exp' in your QGIS vector layer (check 'line_feature.shp' in the 'test_data' folder). If you want to use a defined symbol in your webmap add an attribute 'icon_exp' to your point shapefile and file it with a relative path on your PC or an HTML statement. You can define different icons for each feature. Please check index.html of the webmap to customize popup position regarding your chosen icon. You may find testdata in 'places_few_1_EPSG3857_categorized.shp' in the 'test_data' folder (Donkey designed by Gabriele Malaspina from the thenounproject.com).

If you want to export raster files keep in mind to save them as rendered images prior exporting (values must be integers in the range of 0 to 255).

You can also define a label in the webmap by adding the column 'label_exp' to your layer which will define the text to show in the label.

For single, categorized and graduated symbol point feature layers we are exporting radius (not for polygons), color and opacity. Unfortunately the export of forms and SVG is not embedded at the moment.

If you would like to create a legend you need to add the attributes 'legend_exp' (text to be shown) and 'legend_ico' (icon to be shown) to the desired layer and fill in the link to the icon and a text. Check the test files for details.

The 'locate' button will ask for access to geolocate the browser and will add a marker where the webmap user is found.

The 'address' button will add a geocode/search window in the upper right corner of the webmap.

To define your own basemaps, you need to alter the file qgis2leaf_layerlist and simply add your line to the list. The list consists of the basemap names, a URL for the tiles and an attribution string. If you alter the file you need to reload the plugin to see effects. You can use the [plugin reloader plugin](https://plugins.qgis.org/plugins/plugin_reloader/) for this purpose.

## Installation

* Download the source and place it in the '/.qgis2/python/plugins/qgis2leaf' folder  
  (Windows: 'C:\Users\{username}\.qgis\python\plugins\qgis2leaf')
* Import the plugin using the normal "add plugin" method described [here](http://docs.qgis.org/2.2/en/docs/user_manual/plugins/plugins.html#managing-plugins 'qgis plugins').

## Version_changes
* 2015/04/16 v.1.5.2: solved raster export issues, layer stacking order, and layer visibility
* 2015/04/14 v.1.5.1: Added https://github.com/tomchadwin to authors
* 2015/03/26 v.1.5.0: Major code refactor; tidy output
* 2015/03/17 v.1.4.2: fixed hidden polygon layers; added pen styles
* 2014/12/11 v.1.4.1: bugs for labels fixes. style issue for labels solved
* 2014/12/05 v.1.4: support for label export, embedding of remote WMS servers thanks to [tomchadwin](https://github.com/tomchadwin) and [mtravis](https://github.com/mtravis) for testing
* 2014/12/02 v.1.3: support for blank backgrounds, minor bug fixing
* 2014/12/02 v.1.2: precision export support thanks to [ndawson](http://gis.stackexchange.com/users/28443/ndawson)
* 2014/11/30 v.1.1: multiple basemaps
* 2014/11/29 v.1.0: solved some issues with styles and cluster strategy, added hashes (thanks to https://github.com/mlevans), thanks to [tomchadwin](https://github.com/tomchadwin) for issue solving!
* 2014/09/20 v.0.99b: added settings save and load, user locate and address search (thanks to [Karsten](https://github.com/k4r573n))
* 2014/09/10 v.0.99a: added warning and treatment of unsupported characters in attribute names
* 2014/09/05 v.0.98: additional file for basemap entries
* 2014/08/06 v.0.97: new option to create a legend. supported by [the SPC Ottawa](http://www.spcottawa.on.ca/)
* 2014/08/06 v.0.961: webmap title creation option, improved layer control with pretty names with help from [tomchadwin](https://github.com/tomchadwin) and supported by [the SPC Ottawa](http://www.spcottawa.on.ca/)
* 2014/07/11 v.0.96: cluster support, autohotlinking, wfs support and layer order fix with a lot of help from [tomchadwin](https://github.com/tomchadwin)
* 2014/05/22 v.0.95: raster support for image overlays with thanks to https://github.com/geohacker/leaflet-opacity
* 2014/05/22 v.0.9: support for styles of polygons and polylines
* 2014/05/18 v.0.8.4: define your icon for point shapes, new CDN for the required javascripts
* 2014/05/15 v.0.8.3: style export for graduated, single and categorized symbol point shapefiles
* 2014/05/15 v.0.8.2: style export for graduated and single symbol point shapefiles.
* 2014-05-03 v.0.8.1: new popup creation possibilities
* 2014-05-03 v.0.8: new logo, new UI: toggle visibility
* 2014-05-01 v.0.7: new layer list control for export, non-ASCII character encoding problem solved, fixed folder deletion problem, fixed problem with layer names starting with numbers
* 2014-04-27 v.0.6: fixed installation issues for older python versions (thanks to [mlaloux](https://github.com/mlaloux)), enhanced list of basemap-providers (thanks to [leaflet-providers](https://github.com/leaflet/extras/leaflet-providers/))
* 2014-04-26 v.0.5: new control for full map support, optimized UI (thanks to [mtravis](https://github.com/mtravis), correct attribution for basemaps, new CSS file creation
* 2014-04-25 v.0.4: new layer control for features (thanks to [RCura](https://github.com/RCura)), new GUI with extent setting possibility
* 2014-04-24 v.0.3: new UI with dimension choice for webmap, enhanced HTML structure for better readability
* 2014-04-23 v.0.2: added disambiguation of layer types to avoid break of loop
* 2014-04-22: initial commit

## Tests

You may find testdata in the "test_data" folder.
It was tested on Linux Mint/Ubuntu and Windows 7 with QGIS 2.8.1 and Python 2.7.5+ 

## Contributors

Currently we are working on this project as part of the blog [digital-geography.com](http://www.digital-geography.com 'digital-geography'), [geolicious.](http://www.geolicious.de 'geolicious') and the [Northumberland National Park Authority](https://www.gov.uk/government/organisations/northumberland-national-park-authority 'NNPA.org.uk')
You find additional contributors in the changelog.

## License

```
/***************************************************************************
 *                                                                         *
 *   This program is free software; you can redistribute it and/or modify  *
 *   it under the terms of the GNU General Public License as published by  *
 *   the Free Software Foundation; either version 2 of the License, or     *
 *   (at your option) any later version.                                   *
 *                                                                         *
 ***************************************************************************/
```

