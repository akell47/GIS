# Stormwater Infrastructure Condition
### City of Dunwoody Areas to focus on

City of Dunwoody maintains stormwater infrastructure. Stormwater infrastructure consists of structures and conveyances

Structure:
<img src="https://github.com/akell47/GIS/blob/master/images/structure.JPG"
width="250" height="200"/>
Structure:
<img src="https://github.com/akell47/GIS/blob/master/images/structure2.JPG"
width="180" height="200"/>
<br>
Conveyance:
<img src="https://github.com/akell47/GIS/blob/master/images/conveyance.JPG"
width="250" height="200"/>
<br><br>
Dunwoody hires contractors to assess the condition of the stormwater infrastructure.  These are rated as:<br><br>
-1- IMMEDIATE REPAIR <br>
<p>
<img src="https://github.com/akell47/GIS/blob/master/images/Structure_ImmediateRepair.JPG" width="250" height="200"/>
<img src="https://github.com/akell47/GIS/blob/master/images/Conveyance_ImmediateRepair.JPG" width="250" height="200"/> <br>
</p>
-2- POOR <br>
<p>
<img src="https://github.com/akell47/GIS/blob/master/images/Structure_Poor.JPG"
width="250" height="200"/>
<img src="https://github.com/akell47/GIS/blob/master/images/Conveyance_Poor.JPG"
width="250" height="200"/> <br>
</p>
-3- FAIR <br>
<p>
<img src="https://github.com/akell47/GIS/blob/master/images/Structure_Fair.JPG"
width="250" height="200"/>
<img src="https://github.com/akell47/GIS/blob/master/images/Conveyance_Fair.JPG"
width="250" height="200"/> <br>
</p>
-4- GOOD <br>
<p>
<img src="https://github.com/akell47/GIS/blob/master/images/Structure_Good.JPG"
width="250" height="200"/>
<img src="https://github.com/akell47/GIS/blob/master/images/Conveyance_Good.JPG"
width="250" height="200"/> <br>
</p>
-5- EXCELLENT <br>
<p>
<img src="https://github.com/akell47/GIS/blob/master/images/Structure_Excellent.JPG"
width="250" height="200"/>
<img src="https://github.com/akell47/GIS/blob/master/images/Conveyance_Excellent.JPG"
width="250" height="200"/> <br>
</p>
<br>

## How should the city focus its resources so that it can concentrate on fixing infrastructure conditions in the areas that need it the most? <br>
<p>
This is an overview showing all the structures and conveyances that have a condition assessment value. Dunwoody has been assessing structures by water basin since 2010, when Dunwoody was incorporated as a city. There are three basins left to assess. <br>
Overview: <img src="https://github.com/akell47/GIS/blob/master/images/Overview.JPG"
width="550" height="400"/>
</p>
### The ask for this project: What is the average stormwater condition per subdivision? <br>
<p>
Using Esri's software, ArcMap I spatial joined the subdivision layer to structures and conveyances.  I then exported the data to excel and used a pivot table to summarize counts and averages per each subdivision.  In arcgis online I used arcade expression to average the structure and conveyance averages together for the symbology on the map. <br>
<b>The result:</b> <br>
Dark brown areas have the average condition values of 1 to 3. Gray have better average condition values from 3 to 5. (Dark Gray is the basemap color, no values)<br>
<img src="https://github.com/akell47/GIS/blob/master/images/ConditionbySubdivision.JPG"
width="550" height="400"/> <br>
</p>
#### The problem with this approach
<p>
I can very easily print out the final map, call it done and move on to the next project. However as a GIS Analyst not just a GIS task doer, I am aware of some issues. The subdivision geographies vary greatly, some are larger some much smaller. The amount of features with in each subdivision geography also vary greatly. For example a subdivision called Dunwoody Club Forest has 246 stormwater structures that were given a condition value by assessors which averages to an condition assessment of 4.2. One of the subdivisions with the lowest condition average, Lakeside North, only has 4 structures averaging a condition assessment of 3 and one conveyance with a condition assessment of 1. Averaging 3 and 1 together is a value of 2.  This is another issue with this approach.  With the combined average of the two averages one average with less feature counts can have more influence on the combined average. Lastly, the most obvious issue is that subdivisions do not cover the whole city, such as parks and the GSU Perimeter campus for example.<br>
Lakeside North:
<img src="https://github.com/akell47/GIS/blob/master/images/LakesideNorth.JPG"
width="550" height="300"/>
</p><br>

### Second approach - Geospatial Analysis
<p>
Hot spots and density analysis are a great way to visualize geographic trends.  People tend to
I took three approaches with some of the analysis tools available in Esri's ArcGIS Online.
1 - Hot Spots
2 - Heat Map
3 - Density Clusters
</p>
