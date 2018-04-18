# Automating Creation of FacilityID as String

**Author: Richard Merino**

**Date:3/26/2018**

**Objective/Task: **If existing solution is not already in place, design and implement method for automatic creation of a unique facility ID as a string for tree inventory dataset. Field must be a string and is required for import into Cityworks.

> #### _**\*\*\* Post meeting - Geoevent server is being explored as a solution for easily managing and deploying this automation \*\*\***_ {#post-meeting---geoevent-server-is-being-explored-as-a-solution-for-easily-managing-and-deploying-this-automation-}

**Possible Solutions: **If an existing solution is not currently in use, the following may be considered. These can be divided into SQL and Python solutions:

### **SQL** {#sql}

**Cast number to string on import to Cityworks**

* * **CAST\(“integer\_id” AS CHARACTER\(10\)\) \*/ where 10 is length \*/**
  * **Note: not sure exactly how data is pushed into Cityworks, may not be applicable on import but can be used to cast into new or existing field \(FacilityID as string\)**
  * **Can be scheduled, timed, or triggered if not done on import**
  * ~~**Recommended if import is an explicit action and not ‘automatically’ pulled**~~
* **SQL Jobs scheduled on database OR trigger**
* * **Creation or conversion of int to string using any other conventional SQL method can be scheduled as a job using a job scheduler for the database.**
  * **Likely the best option as there would be less points of failure, data is already in SQL database, and would run on server without need for dedicated machine**
  * **Oracle syntax for scheduler:**
  * > `BEGIN DBMS_SCHEDULER.CREATE_JOB ( job_name => 'update_sales', job_type => 'STORED_PROCEDURE', job_action => 'OPS.SALES_PKG.UPDATE_SALES_SUMMARY', start_date => '28-APR-08 07.00.00 PM Australia/Sydney', repeat_interval => 'FREQ=DAILY;INTERVAL=2', /* every other day */ end_date => '20-NOV-08 07.00.00 PM Australia/Sydney', auto_drop => FALSE, job_class => 'batch_update_jobs', comments => 'My new job'); END; /`

### **Python** {#pythoncan-be-run-as-continuously-running-script-or-scheduled-script-}

**\(Can be run as continuously running script or scheduled script\)**

* **The RESTful way**
* * **Uses the REST API to access the feature service**
  * **The data accessed will be in json format**
  * **In order to calculate the FacilityID field, the field calculator URL \(REST service\) must be requested in the script as well**
  * **Adds room for more error on crucial step with calculator URL - **~~**calculating exclusively with python will require entire json text to be read into memory?**~~
* **Modifying at source as feature service is streamed \(See diagram on top\)**
* * **Note any potential problems with modifying at source, running on server vs. on dedicated machine**
  * **Can be run as continuous script OR scheduled by OS, scheduled may be better for this option**
  * **May be the best python option; imitates a user manually doing task every x minutes or on scheduled time**
* **Using the Python API to access portal content and post changes \(See diagram on bottom\)**
* * **Note any potential problems with persistent authentication, dedicating a machine to run, etc.**
  * **Can be run as continuous script OR scheduled by OS, continuous may be better for this option due to authentication**
  * **Authentication, even if just once before run, may cause problems with reliability of script**

![](https://lh5.googleusercontent.com/x7-hi_sANEVDeYX07SrCZu5yUy5ByC9Ev7vz-Ey9D-T67ukwR5L_pSbGjhWwsnuxE77UhFaFnsDoVisHs-yBBbn6hy_YViSJxfPko6MmbrKL-06x9OIStbSLsKGBLlT9xeiWovF3)

