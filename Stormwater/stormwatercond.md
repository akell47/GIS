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
</p>
Overview: <img src="https://github.com/akell47/GIS/blob/master/images/Overview.JPG"
width="550" height="400"/><br>

### The ask for this project: What is the average stormwater condition per subdivision? <br>
<p>
Using Esri's software, ArcMap I spatial joined the subdivision layer to structures and conveyances.  I then exported the data to excel and used a pivot table to summarize counts and averages per each subdivision.  I joined the summary table back to the subdivision layer and published the layers to ArcGIS Online. In ArcGIS online I used arcade expression to average the structure and conveyance averages together for the symbology on the map. <br>
<b>The result:</b> <br>
Dark brown areas have the average condition values of 1 to 3. Gray have better average condition values from 3 to 5. (Dark Gray is the basemap color, no values)<br>
</p>
<img src="https://github.com/akell47/GIS/blob/master/images/ConditionbySubdivision.JPG"
width="550" height="400"/> <br>

#### The problem with this approach
<p>
I can very easily print out the final map, call it done and move on to the next project. However as a GIS Analyst not just a GIS task doer, I am aware of some issues. The subdivision geographies vary greatly, some are larger some much smaller. The amount of features with in each subdivision geography also vary greatly. For example a subdivision called Dunwoody Club Forest has 246 stormwater structures that were given a condition value by assessors which averages to an condition assessment of 4.2. One of the subdivisions with the lowest condition average, Lakeside North, only has 4 structures averaging a condition assessment of 3 and one conveyance with a condition assessment of 1. Averaging 3 and 1 together is a value of 2.  This is another issue with this approach.  With the combined average of the two averages one average with less feature counts can have more influence on the combined average. Lastly, the most obvious issue is that subdivisions do not cover the whole city, such as parks and the GSU Perimeter campus for example.<br>
</p>
Lakeside North:
<img src="https://github.com/akell47/GIS/blob/master/images/LakesideNorth.JPG"
width="550" height="300"/>
<br>

### Second approach - Geospatial Analysis

Hot spots and density analysis are a great way to visualize geographic trends.  People tend to visualize clusters where perhaps there are not clusters. For example is there a cluster in the North West corner of the city? Using geospatial analysis tools, you can be sure of actual clusters.
I took three approaches with some of the analysis tools available in Esri's ArcGIS Online:
- Hot Spots
- Heat Map
- Point Density
<br><br>
The maps are just on the stormwater structures, not the conveyances.  The point is to demonstrate different ways to visualize clustering.  For this project it was determined that this approach is not most fitting, for making decisions of where to concentrate repair efforts, so just the structures are shown here.
<br><br>
<b>1 - Hot Spots </b><br>
Hot Spots: <img src="https://github.com/akell47/GIS/blob/master/images/HotSpots.JPG"
width="550" height="400"/> <br>
When using numerical attribute of points, the hot spots are points rather than a gridded hot spot layer.  We are looking for concentrations of 3, 4, and 5 values of stromwater structure. The resulting map shows where there are clusters of poor structure conditions. The hot spot tool is going to automatically assign higher value with greater weight.  Since 1 is poor condition and 5 is excellent condition, for this analysis tool a separate column was used with these condition values reversed so that 1 is now "5" and has greater influence in finding hot spots of poorer conditions. That value combined with geographic distances produces the hot spots. The Hot Spot analysis uses a formula behind the hood known as the Getis-Ord local statistic. The output is a map of Z scores. The Z scores are the tail ends of the distributed data with significant spatial clustering. Z scores near 0 show no spatial clustering.
<br><br>
<b> 2 - Heat Map </b><br>
Heat Map: <img src="https://github.com/akell47/GIS/blob/master/images/HeatMap.JPG"
width="550" height="400"/> <br>
That's right, a Heat Map is not a Hot Spot Map. Hot Spot map tells you where there are statistically significant clusters, where as a heat map is a more basic visualization of clusters. In this map a filter was set where condition is greater than 2.  Poorer conditions do not have greater weight in the heat map here. All conditions of 3, 4, and 5 are treated equally and the heat map shows where there are more of these points.
<br><br>
<b>3 - Density Clusters</b> <br>
Point Density: <img src="https://github.com/akell47/GIS/blob/master/images/PointDensity.JPG"
width="550" height="400"/> <br>
Again, this style shows where features are concentrated. Reddish Pink areas have a concentration of structures with less than good conditions and darker red areas have the greatest concentration of stormwater structures with poorer conditions.  This approach smooths out a collection of points into a density polygon. This tool helps to simplify the points and visualize density in a more visually appealing way. Point Density also takes a count field as a parameter.  Of the three Density tools, this one is the best for this purpose. This shows areas with higher concentrations of stormwater structures with more importance placed on the worse conditions.  This way you can see areas that have a concentration of the worst conditions in a way that is easier to understand than Hot Spots and take into account the condition value unlike the Heat Map.
<br><br>

### Final approach - Spatial Selections

The benefit of the density maps is that one can definitively determine areas that have a cluster of poorer stormwater infrastructure conditions.  This helps minimize subjectivity of visual analysis.  One can look at the north east corner for example and say there is a cluster of structures that need immediate repair, however in actuality there is not a cluster given the other areas. However, the field crew need to know which structures exactly they can repair.  The density maps are cool, but they do not exactly aid in determining actual work orders.  Applications of density maps are better utilized when determining focus areas with a shifting population, such as crime, poverty, fires, or customer marketing.  The structures are in fixed locations.  We need to find which structures and conveyances Public Works can access and repair. <br><br>
<b>The city can only repair infrastructure in residential zoned areas and in the right of way. </b> <br>
Creating Right of Way layer - I used the symmetrical difference tool with the zoning layer which was derived from parcel layer and the city boundary layer. The resulting difference is roughly the right of way.  <br>
Residential layer - This layer is residential areas that have public roads. There are areas that have townhomes but have public roads. Structures on property with private roads are responsibility of the landowners.
Right ofWay: <img src="https://github.com/akell47/GIS/blob/master/images/RightofWay.JPG"
width="450" height="400"/> <br>
Structures and Conveyances that intersect the Residential layer and the Right of Way layer are the starting point for Stormwater Infrastructure repairs. 
