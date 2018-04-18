# Notes

{% embed data="{\"url\":\"https://ral.maps.arcgis.com/apps/webappviewer/index.html?id=1ce5f7a952204b028f413d6f26107d55\",\"type\":\"link\",\"title\":\"ArcGIS Web Application\",\"icon\":{\"type\":\"icon\",\"url\":\"https://ral.maps.arcgis.com/apps/webappviewer/images/shortcut.ico\",\"aspectRatio\":0}}" %}

Don't forget the \[https://\] when deploying to allow location tracking.

### Try vector tiles for features so that labels are dynamic\(er\) in AGOL

* May need to get Ryan to publish as I do not have the rights
* Got rights to publish
* Works great but consider the update process - tiles not streamed

### Symbology for trails

* Top line layer - Marker fill by surface type. Circles and/or X's?
  * Marker placement &gt; placement template controls distance between markers
* Bottom line layer - larger size based on blaze color, makes translucent? 
* If and when structures are added, we can adopt a marker and color type for it.

![Example of how it could look for a blue blaze trail with natural surface type](../../.gitbook/assets/trail_symbol.PNG)

### Labels

* Pay attention to label scales
* White text, black 0.5 halo
* Include mileage for trail/main segment in label.
  * Generate with add geometry script

### Map tile creation

* Tiling Scheme should be set at WGS84 for greater LoD. Up to 22, 23 is max.
  * IN ORDER TO DO THIS - MUST REPROJECT ALL TO MATCH
* Tiling scheme can be created from rasters... for vectors it must be MXD?



