# Richard's To Do Checklist

> Run current LOS tool at multiple distances:
>
> * Run tool at network and calc at 0.5mi, 1mi, and 2 mi.
> * PROBLEM: calc seems same &gt; start from scratch on calcs each time
>   * How are parks per person being counted right now??? why is it 1/pop sum \(INVESTIGATE\)
>   * When a Block centroid has access to multiple access points for the same park, does the current model assume they are multiple parks?
>     * Ask others and also investigate the code to check if this is the case
> * Potential root causes for the problem:
>   * Distance is actually hard coded in the LOS scripts
>     * Likely not the case - keyword sweep yields nothing and it makes the most sense that distances are set at the network analysis level
>   * The script is not actually overwriting the fields that have already been calculated, or in other words the fail safe check is failing in the python script
>     * This is possible - in order to verify we should run from scratch each time. At the very least check it once to your current results. _**`The original output has been saved in the EBPA_Block_model pro project in your documents directory. When running from scratch, make sure to double check the starting data (Census Blocks) as well. It is possible that the fields have already been populated?`**_
>
>
>
> Tie park experience to access points\(uploaded on AGOL\), investigate creation of new routes, 
>
> _**Look into creating tool that lists all amenities for a given park: at first glance it looks like we can through the layer on the map and cursor through with a conditional and will return the field name if the condition is met - doesn't even necessarily have to be a map, but the spatial component of comparing would be nice.**_
>
> 1. Consolidate from park locator into park polygons or just use points \(clean up the park locator data\)
>    1. Would have to clean data up. Maybe have each park hold an array
> 2. Turn dataset into geojson?
> 3. Have two containers that hold info for park you select where you can compare two?
> 4. On click, check condition for amenity fields, if pass show in container
>    1. maybe pass all to temp arr then display from temp arr
>
>
>
>
>
> **In order to create AGOL custom widgets and apps \(the right way\)**
>
> * **Typescript**
>   * Type annotation for parameters and classes
> * **Classes**
>   * Constructors
>   * Instances with typescript
>     * extend
>     * super
> * **ES6 Arrow Functions**
> * **node.js**
>   * virtual DOM
> * **npm**
>   * overhead packaging
> * **Dojo** \(2\)
>   * one letter variable functions
>   * protected functions / private / public
> * **Dijit \(Dojo's UI Library\)**
>   * requires dojo core & dojo base
>
> ### AGOL Stack:
>
> * Back - AGOL Hosted Portal / REST API
> * Front - Dojo toolkit

### Here's what you need to catch up writing on

* \[ \] REST API
  * \[ \] You looked a little at this, there will definitely be more later
* \[ \] Document Processes
  * \[ p \] Try to document creating your apps to show best practices and such
* \[ \] Create documentation on types of apps and when it is best to use them, especially ArcGIS packages, general considerations when going to build such as length of time, difficulty, cost considerations, software used, data sources, delivery and audience
  * \[ \] Crowd Source
  * \[ \] Web App Builder
  * \[ \] Story Maps
  * \[ \] Mobile Maps
  * \[ \] Custom \(Leaflet or otherwise\) &gt; You need a method of delivery - it has to sit on a server somewhere
* Occupy empty pages you placed with notes and research you've conducted on said topic
* Are there any tools/services you looked at that are worth documenting?



