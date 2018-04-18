# Working

{% embed data="{\"url\":\"https://ral.maps.arcgis.com/apps/webappviewer/index.html?id=1ce5f7a952204b028f413d6f26107d55\",\"type\":\"link\",\"title\":\"ArcGIS Web Application\",\"icon\":{\"type\":\"icon\",\"url\":\"https://ral.maps.arcgis.com/apps/webappviewer/images/shortcut.ico\",\"aspectRatio\":0}}" %}

Don't forget the \[https://\] when deploying to allow location tracking.

## Work track

### Try vector tiles for features so that labels are dynamic\(er\) in AGOL

* May need to get Ryan to publish as I do not have the rights
* Got rights to publish
* Works great but consider the update process - tiles not streamed

### Symbology for trails

* \(Only for Vector Tiling\) Top line layer - Marker fill by surface type. Circles and/or X's?
  * Marker placement &gt; placement template controls distance between markers
* Bottom line layer - larger size based on blaze color, makes translucent? 
* If and when structures are added, we can adopt a marker and color type for it.

![Example of how it could look for a blue blaze trail with natural surface type](../../.gitbook/assets/trail_symbol.PNG)

### Labels

* Pay attention to label scales
* White text, black 0.5 halo
* Include mileage for trail/main segment in label.
  * Generate with add geometry script or manual append 

### Map tile creation - a no go?

* ~~Tiling Scheme should be set at WGS84 for greater LoD. Up to 22, 23 is max.~~
  * ~~IN ORDER TO DO THIS - MUST REPROJECT ALL TO MATCH~~
* Tiling scheme can be created from rasters...[ for vectors it must be MXD?](../../data/map-tiling.md)
* Default tiling cache scheme works fine, custom may be more trouble than its worth
* Have had intermittent issues displaying map tiles on mobile browsers [SEE BUG HERE](../../data/map-tiling.md#less!-bug:-map-tiles-not-displaying-properly-on-some-mobile-devices!-greater)

### Adjusting Label Scales - Fixing

A work around to messy labels is to have over arching labels for lower zoom levels and set the visibility for line labels \(on line labels\) at higher zoom levels. This will reduce clutter. You can set zoom level for the location tracking widget - it would be a good idea to match the zoom level to which it calls to with the zoom level when line labels are rendered. The expected result would be &gt; User presses locate button, zooms to user who is on trail, trail is clearly labeled with name, blaze, mileage. User will be able to navigate which direction.



