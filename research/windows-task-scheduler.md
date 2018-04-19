# Windows Task Scheduler

**Author: Richard Merino**

**Date: 3/27/2018**

**Windows Task Scheduler**

**Purpose: **Summarize Windows Task Scheduler - its potential uses, benefits, configuration with python scripting, and considerations. This may help pave the way for establishing workflows and brainstorm more potential uses.

**What is it?** This service is pre-installed on several Windows distributions and will run programs or workflows on prescribed times as specified by the user OR on action triggers. Most Windows machines will have tasks already scheduled for updates and vital system services. Task scheduler can be accessed by searching for “task scheduler” in the Windows search menu. How and why should we use it? In our context, this is a valuable tool for automating data creation, datacleanup, recurring workflows, and data administration. There are many things to address when hard coding time and operating system integration into scripts - this eliminates those factors and can be more reliable.

**Example cases:**

**● Data creation **- schedule creation of spatial dataset based on dynamically changing text data

**● Data cleanup **- schedule conversion of FacilityID as integer to string

**● Recurring workflows **- schedule statistical analysis and reporting; schedule ModelBuilder

**● Data administration** - schedule backup of AGOL data; backup local data when locking machine

**Configuring with Python:** The setup wizard when creating a task is highly intuitive, but creating a Python action is not as straightforward as setting the action to open your script. Task Scheduler prefers explicit locations. The best settings for python scripts seems to be:

**Action **: Start a program

**Program/script:** &lt;Location of your python.exe or pythonw.exe for silent scripts \(no console popup\)&gt;

**Add arguments :** &lt;”Explicit location and script name in quotes”&gt;

**Start in :** &lt;Location of the python script&gt;

**Example Settings:**

**Action :** Start a program

**Program/script: **C:\Python27\python.exe

**Add arguments :** "C:\Users\Richard\Desktop\DATA\Scripts\ScheduledTest.py"

**Start in : **C:\Users\Richard\Desktop\DATA\Scripts

**Considerations:** Although tasks can be scheduled to retry at fail, pick up if it misses a time, run in the background, etc - it would be best to run vital scripts on a server distribution of Windows if possible. This may not be necessary for us as any needed pushes can be done manually if a hiccup should occur.

**Helpful Links:**

**Scheduling a python script:**

{% embed data="{\"url\":\"https://blogs.esri.com/esri/arcgis/2013/07/30/scheduling-a-scrip/\r\",\"type\":\"link\",\"title\":\"Scheduling a Python script or model to run at a prescribed time\",\"icon\":{\"type\":\"icon\",\"url\":\"https://www.esri.com/favicon.ico\",\"aspectRatio\":0}}" %}

https://communityhub.esriuk.com/technicalsupport/2016/8/31/scheduling-a-modelbuilder-model-using-task-scheduler

**Scheduling a model:**

{% embed data="{\"url\":\"http://pro.arcgis.com/en/pro-app/help/analysis/geoprocessing/modelbuilder/scheduling-a-model-run.htm\",\"type\":\"link\",\"title\":\"Schedule a model—ArcGIS Pro \| ArcGIS Desktop\",\"description\":\"You may want to have a geoprocessing model run at a specific time of day or set the model to run repeatedly at some time interval.\",\"icon\":{\"type\":\"icon\",\"url\":\"http://pro.arcgis.com/assets/img/favicon.ico\",\"aspectRatio\":0}}" %}

