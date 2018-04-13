# ArcGIS Python API

## Important Code Blocks for working with the Python API {#Important-Code-Blocks-for-working-with-the-Python-API}

Richard Merino \| merinogeospatial@gmail.com \| richard.merino@raleighnc.gov

Content Manager reference material - [https://esri.github.io/arcgis-python-api/apidoc/html/arcgis.gis.toc.html\#contentmanager](https://esri.github.io/arcgis-python-api/apidoc/html/arcgis.gis.toc.html#contentmanager)

The blocks below can be use as building blocks/reference to create scripts for creating automated processes. This notebook contains necessary blocks for extracting and backing up your feature layers. Can be written in time loop after authentication for persistently running script. Note that federated logins must use this authentication framework for now, username and password authentication not working for our type of login

For updating feature layers, refer to - [https://developers.arcgis.com/python/guide/editing-features/](https://developers.arcgis.com/python/guide/editing-features/)In \[3\]:

```text
# IMPORT DEPENDENCIES
import arcgis
from arcgis.gis import GIS
from IPython.display import display
print ("Import Successful")
```

```text
Import Successful
```

In \[4\]:

```text
# AUTHENTICATE WITH OAUTH2
gis = GIS("https://ral.maps.arcgis.com", client_id='UXzZvlwDeph2dkcN')
print("Successfully logged in as: " + gis.properties.user.username)
```

```text
Please sign in to your GIS and paste the code that is obtained below.
If a web browser does not automatically open, please navigate to the URL below yourself instead.
Opening web browser to navigate to: https://ral.maps.arcgis.com/sharing/rest/oauth2/authorize?client_id=UXzZvlwDeph2dkcN&response_type=code&expiration=-1&redirect_uri=urn%3Aietf%3Awg%3Aoauth%3A2.0%3Aoob
Enter code obtained on signing in using SAML: ········
Successfully logged in as: richard.merino@raleighnc.gov_ral
```

In \[5\]:

```text
type(gis.content) # check content manager, unnecessary
```

Out\[5\]:

```text
arcgis.gis.ContentManager
```

In \[6\]:

```text
# CREATE CONTENT QUERY, RETURNS LIST OF OBJECTS
search_result = gis.content.search(query="owner:richard.merino@raleighnc.gov_ral", item_type="Feature Layer")
search_result
```

Out\[6\]:

```text
[<Item title:"Public Art Installations" type:Feature Layer Collection owner:richard.merino@raleighnc.gov_ral>,
 <Item title:"Tree_subset(TEST)" type:Feature Layer Collection owner:richard.merino@raleighnc.gov_ral>]
```

In \[7\]:

```text
# DISPLAYS SEARCH RESULTS 
from IPython.display import display
for item in search_result:
    display(item)
```

![](data:image/png;base64,R0lGODlhBQAFAID/AMDAwAAAACH5BAEAAAAALAAAAAAFAAUAQAIEhI+pWAA7)

[**Public Art Installations** ](https://ral.maps.arcgis.com/home/item.html?id=d5b73a2b645e47a9910273f2ae2932dc)

![](https://ral.maps.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/featureshosted16.png)

Feature Layer Collection by richard.merino@raleighnc.gov\_ral   
Last Modified: March 28, 2018   
0 comments, 11 views

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAACFCAIAAACR/CB7AAAACXBIWXMAAA7EAAAOxAGVKw4bAAABbElEQVR4nO3SwQ3AIBDAsNL9dz6WIEJC9gR5ZM3MB6f9twN4k7FIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSGy4dQQHgizXSQAAAABJRU5ErkJggg==)

[**Tree\_subset\(TEST\)** ](https://ral.maps.arcgis.com/home/item.html?id=207450656b6641618994413617fdcbb5)

![](https://ral.maps.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/featureshosted16.png)

Feature Layer Collection by richard.merino@raleighnc.gov\_ral   
Last Modified: March 22, 2018   
0 comments, 11 views

## Item objects are to be called by Item ID {#Item-objects-are-to-be-called-by-Item-ID}

In \[8\]:

```text
# GET ITEM ID
tree_data = search_result[1]
tree_data_id = tree_data.id
print(tree_data_id)
```

```text
207450656b6641618994413617fdcbb5
```

In \[20\]:

```text
"""# PUTTING ALL IDs FROM QUERY INTO LIST
item_id_list = []
for i in search_result:
    item_id_list.append(gis.content.get(str(i.id)))
print(item_id_list)"""

# GETTING ID IS UNNCESSARY - PULL STRAIGHT FROM OBJECT LIST
for i in search_result:
    i.download(save_path='C:\\Users\\merinor\\Documents\\Data')
print ("Items saved in specified location")
    
```

```text
Items saved in specified location
```

In \[7\]:

```text
# SET VARIABLE TO ACCESS SPECIFIED ITEM
get_item = gis.content.get('207450656b6641618994413617fdcbb5')
get_item
```

Out\[7\]:

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAMgAAACFCAIAAACR/CB7AAAACXBIWXMAAA7EAAAOxAGVKw4bAAABbElEQVR4nO3SwQ3AIBDAsNL9dz6WIEJC9gR5ZM3MB6f9twN4k7FIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSBiLhLFIGIuEsUgYi4SxSGy4dQQHgizXSQAAAABJRU5ErkJggg==)

[**Tree\_subset\(TEST\)** ](https://ral.maps.arcgis.com/home/item.html?id=207450656b6641618994413617fdcbb5)

![](https://ral.maps.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/featureshosted16.png)

Feature Layer Collection by richard.merino@raleighnc.gov\_ral   
Last Modified: March 22, 2018   
0 comments, 27 viewsIn \[8\]:

```text
# RETURNS JSON FORMAT METADATA - NO SPATIAL DATA INCLUDED, DO NOT USE TO BACKUP
data = get_item.get_data()
data
```

Out\[8\]:

```text
{'layers': [{'id': 0,
   'layerDefinition': {'defaultVisibility': True},
   'popupInfo': {'description': None,
    'fieldInfos': [{'fieldName': 'FID',
      'isEditable': False,
      'label': 'FID',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': False},
     {'fieldName': 'ROUTE',
      'isEditable': True,
      'label': 'ROUTE',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'UNIQUE_ID',
      'format': {'digitSeparator': True, 'places': 0},
      'isEditable': True,
      'label': 'UNIQUE_ID',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'XCO',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'XCO',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'YCO',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'YCO',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'ZCO',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'ZCO',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'SURVEY',
      'isEditable': True,
      'label': 'SURVEY',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'FACILITYID',
      'isEditable': True,
      'label': 'FACILITYID',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'WARRANTYDA',
      'format': {'dateFormat': 'shortDateShortTime'},
      'isEditable': True,
      'label': 'WARRANTYDA',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'SPECIES',
      'isEditable': True,
      'label': 'SPECIES',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'COND',
      'isEditable': True,
      'label': 'COND',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'DBH',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'DBH',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'GRATE',
      'isEditable': True,
      'label': 'GRATE',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'GENUS',
      'isEditable': True,
      'label': 'GENUS',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'CULTIVAR',
      'isEditable': True,
      'label': 'CULTIVAR',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'ITEM_ID',
      'isEditable': True,
      'label': 'ITEM_ID',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'SPECIES_CN',
      'isEditable': True,
      'label': 'SPECIES_CN',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'INST_DATE',
      'isEditable': True,
      'label': 'INST_DATE',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'STEMCOUNT',
      'format': {'digitSeparator': True, 'places': 0},
      'isEditable': True,
      'label': 'STEMCOUNT',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'Worst_Est_',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'Worst_Est_',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'Aver_Est_A',
      'format': {'digitSeparator': True, 'places': 2},
      'isEditable': True,
      'label': 'Aver_Est_A',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'COMBINED',
      'isEditable': True,
      'label': 'COMBINED',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'INV_DATE',
      'format': {'dateFormat': 'shortDateShortTime'},
      'isEditable': True,
      'label': 'INV_DATE',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'INV_TIME',
      'isEditable': True,
      'label': 'INV_TIME',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'EDITTIME',
      'format': {'dateFormat': 'shortDateShortTime'},
      'isEditable': True,
      'label': 'EDITTIME',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'SOURCE',
      'isEditable': True,
      'label': 'SOURCE',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'STATUS',
      'isEditable': True,
      'label': 'STATUS',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'F2013__Col',
      'format': {'digitSeparator': True, 'places': 0},
      'isEditable': True,
      'label': 'F2013__Col',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True},
     {'fieldName': 'ID_STRING',
      'isEditable': True,
      'label': 'ID_STRING',
      'stringFieldOption': 'textbox',
      'tooltip': '',
      'visible': True}],
    'mediaInfos': [],
    'showAttachments': True,
    'title': 'Tree_subset(TEST)'}}]}
```

In \[9\]:

```text
# WRITE METADATA TO JSON
import json
with open('data.json', 'w') as file:
  json.dump(data, file, ensure_ascii=False)
print ("JSON Backup created in location of this notebook") 
# Does not contain spatial data > find way to export geojson
```

```text
JSON Backup created in location of this notebook
```

In \[17\]:

```text
# DOWNLOADS ITEM TO PATH (DOES NOT CHANGE FORMAT)
get_item.download(save_path='C:\\Users\\Richard\\Desktop\\DATA')
print ("Item saved in specified location")
```

```text
Item saved in location of this notebook
```

In \[20\]:

```text
#EXPORTS SPECIFIED ITEM TO SPECIFIED FORMAT - WILL SAVE IN YOUR AGOL CONTENTS LOCATION
get_item.export('Tree_subset(TEST)', 'GeoJson', parameters=None, wait=True)
```

Out\[20\]:

![](http://static.arcgis.com/images/desktopapp.png)

[**Tree\_subset\(TEST\)** ](https://ral.maps.arcgis.com/home/item.html?id=2fadeab367f440adb440caf2d3e9bbec)

![](https://ral.maps.arcgis.com/home/js/jsapi/esri/css/images/item_type_icons/layers16.png)

GeoJson by richard.merino@raleighnc.gov\_ral   
Last Modified: March 27, 2018   
0 comments, 0 viewsIn \[23\]:

```text
search_result2 = gis.content.search(query="owner:richard.merino@raleighnc.gov_ral", item_type="GeoJSON")
search_result2
```

Out\[23\]:

```text
[<Item title:"Tree_subset(TEST)" type:GeoJson owner:richard.merino@raleighnc.gov_ral>]
```

\# INTERATION OVER DICTIONARIES - .item creates dictionary as tuple to be unpacked for key,value in dictionary.items\(\): print\(key, 'corresponds to', value\)

