---
description: >-
  Schedule your content to back up from cloud to your machine or OneDrive with
  the Python API
---

# Automating ArcGIS Online Backups

First set up the ArcGIS API for Python \| [https://developers.arcgis.com/python/guide/install-and-set-up/](https://developers.arcgis.com/python/guide/install-and-set-up/)

Think about the steps that need to happen for backing up. The rough logic can be found below: 

![Turns out that the code does not have to create the items list to be used. When running the query, it returns a list of objects. You are able to reference objects without needing to extract the item id. Because we are using a federated log in, currently authenticating with OAuth2 is supported. With of this extra step of pasting your key in, it would be best to run the scheduler after logging in.](../.gitbook/assets/pythonbackupapi.PNG)

## AGOL Backup - Python API {#AGOL-Backup---Python-API}

3.29.2018 \| Needs error handling, needs logging, notifications

Richard Merino \| richard.merino@raleighnc.gov \| merinogeospatial@gmail.comIn \[24\]:

```text
# Import Dependencies
import time
import arcgis
from arcgis.gis import GIS
from IPython.display import display
from apscheduler.schedulers.blocking import BlockingScheduler
print ("Import Successful")
```

```text
Import Successful
```

In \[2\]:

```text
# Authenticate AGOL with OAuth2
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

In \[25\]:

```text
# Global Variables
scheduler = BlockingScheduler()
time_stamp = (time.strftime("%m/%d/%Y") + " >>> " + time.strftime("%H:%M:%S"))
```

In \[ \]:

```text
# Create backup function to schedule
def scheduled_backup():
    # Grab all hosted feature layers
    my_featurelayers = gis.content.search(query="owner:richard.merino@raleighnc.gov_ral", item_type="Feature Layer")

    # Convert all hosted feature layers to choice of format, in my case GeoJson
    for i in my_featurelayers:
        i.export(i.title, 'GeoJson', parameters=None, wait=True)
        print (time_stamp + " | %s has sucessfully exported" % (i.title))

    # Grab all newly created GeoJson
    my_geojsons = gis.content.search(query="owner:richard.merino@raleighnc.gov_ral", item_type="GEOJson")
    for i in my_geojsons:
        i.download(save_path='C:\\Users\\merinor\\Documents\\Data')
    print (time_stamp + " | Items saved in specified location")

    delete_items(my_geojsons)
    print (time_stamp + " | Temporary exports have been deleted")

    #!#!#! Generate log locally or place in AGOL, append to log each iteration #!#!#!
    
    return "Back up completed on" + time_stamp
    
# Starts schedule session
scheduler.add_job(scheduled_backup, 'interval', hours=12)
scheduler.start()
```

