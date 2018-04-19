# Windows Task Scheduler

**Author: Richard Merino

**Date: 3/27/2018

**Windows Task Scheduler

**Purpose: **Summarize Windows Task Scheduler - its potential uses, benefits, configuration with python

**What is it?** This service is pre-installed on several Windows distributions and will run programs or

**Example cases:

**● Data creation **- schedule creation of spatial dataset based on dynamically changing text data

**● Data cleanup **- schedule conversion of FacilityID as integer to string

**● Recurring workflows **- schedule statistical analysis and reporting; schedule ModelBuilder

**● Data administration** - schedule backup of AGOL data; backup local data when locking machine

**Configuring with Python:** The setup wizard when creating a task is highly intuitive, but creating a Python

**Action **: Start a program

**Program/script:** &lt;Location of your python.exe or pythonw.exe for silent scripts \(no console popup\)&gt;

**Add arguments :** &lt;”Explicit location and script name in quotes”&gt;

**Start in :** &lt;Location of the python script&gt;

**Example Settings:

**Action :** Start a program

**Program/script: **C:\Python27\python.exe

**Add arguments :** "C:\Users\Richard\Desktop\DATA\Scripts\ScheduledTest.py"

**Start in : **C:\Users\Richard\Desktop\DATA\Scripts

**Considerations:** Although tasks can be scheduled to retry at fail, pick up if it misses a time, run in the

**Helpful Links:

**Scheduling a python script:

{% embed data="{\"url\":\"https://blogs.esri.com/esri/arcgis/2013/07/30/scheduling-a-scrip/\r\",\"type\":\"link\",\"title\":\"Scheduling a Python script or model to run at a prescribed time\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.esri.com/favicon.ico\",\"aspectRatio\":0}}" %}

https://communityhub.esriuk.com/technicalsupport/2016/8/31/scheduling-a-modelbuilder-model-using-tas

**Scheduling a model:

{% embed data="{\"url\":\"http://pro.arcgis.com/en/pro-app/help/analysis/geoprocessing/modelbuilder/scheduling-a-model-run.htm\",\"type\":\"link\",\"title\":\"Schedule a model—ArcGIS Pro \| ArcGIS Desktop\",\"description\":\"You may want to have a geoprocessing model run at a specific time of day or set the model to run repeatedly at some time interval.\",\"icon\":{\"type\":\"icon\",\"url\":\"http://pro.arcgis.com/assets/img/favicon.ico\",\"aspectRatio\":0}}" %}
