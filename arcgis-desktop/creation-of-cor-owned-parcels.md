# Creation of COR-owned parcels

**Author: Richard Merino**

**Date: 3/21/2018**

**Objective/Task:** Create a new feature class of all city-owned parcels that include: maintenance manager, address, park maintenance district, parcel area in both acres and square feet, parcel id, PIN number and real estate id.

**Datasets Used:**

* Real Estate Spreadsheet from Greg Laughinghouse
* Wake County Parcels

**Software Used:**

* ArcGIS Pro
* Excel

**Steps Taken:**

1. Clean the real estate spreadsheet - remove spaces from headers
2. Convert .xls to .dbf
3. Inner join .dbf to Wake County Parcels by real estate ID \(REID\)
4. Turn off irrelevant fields/rename fields
5. Export new feature class from joined layer \(Copy Features in geoprocessing toolbox\)

**Notes:**

* 1312 out of 1363 join matched base on REID
* Must remove “$” in sheet file name in order for conversion to .dbf to work

