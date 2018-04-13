# Creation of Parcels Containing Parks

**Author: Richard Merino**

**Date: 3/21/2018**

**Objective/Task:**Create a new feature class of all parcels containing parks that include: park name, park id, park area in square feet and acres, parcel id, PIN number, and real estate id.

**Datasets Used:**

* PRCR Parks Data
* Wake County Parcels

**Software Used:**

* ArcGIS Pro

**Steps Taken:**

1. Select features by locations - select all parcels that contain the centers of parks \(“have their center in” relationship\)
2. Export selection as a base feature class to append/remove from
3. Adjust symbology to allow distinction of parcels that were not picked up or should be deleted
4. 1. If parcel needs to be added - select the parcel and use the append tool
   2. If parcel needs to be removed - simply select and delete the feature
5. Once proper geometry is established, use a spatial join to combine the subsetted parcels with the parks \(“intersect” method\). You may remove irrelevant fields in this step in the spatial join menu

**Notes:**

* Note that the parks dataset is not snapped to the parcel dataset
* Not all parks will be in parcels
* Parks may span more than one parcel or part of one parcel
* Due to the variables mentioned above- step 3 is important as parcels

