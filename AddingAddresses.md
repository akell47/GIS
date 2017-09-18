# Parallel Evenly Spaced points
### Adding Apartment Addresses

We have an apartment complex and need to add addresses to them. The private roads within the apartment complex are private roads. We have addresses of the buildings but we are missing the unit numbers. The unit numbers are part of the street number of the address.  Unit 1535, is `1535 [Street Name].`
## Tools:
ArcGIS Pro.
Existing project opened into ArcGIS Pro project environment

## Execution:
1- Import mxd into Pro. <br>
#### Add address points <br>
<b>1-</b> Create line feature for points to be added upon. <br>
    Open Create Feature Class Tool > New Line Template in Layers <br>
    <br>
<b>2-</b> Determine QB Direction to make all lines parallel<br>
    Start to draw the line, move mouse out to desired angle. Don't finish the line, instead right click > Direction > Copy Direction. <br>
    http://pro.arcgis.com/en/pro-app/help/editing/direction-formats-for-editing.htm <br>
    http://pro.arcgis.com/en/pro-app/help/editing/specify-a-direction-and-distance.htm <br>
  <sub>
    East Direction: `N90-00-00E`<br>
    West Direction: `S90-00-00W`<br>
    North Direction: `N0-00-00E`<br>
    South Direction: `S0-00-00W`<br>
  </sub>
  <sub><sub>
    Notes My Settings:
    Building 8 Slight NE Direction: `N3-32-22W`,
    Slight SE Direction: `S4-17-21E`<br>
    Building 12 SW Direction: `S63-48-43W`,
    NE Direction: `N64-03-28E`<br>
    Potomac Buildings SE Direction: `S3-40-04E`,
    NW Direction: `N4-30-50W`<br>
    Building 18 NE Direction: `N86-50-57E`,
    SW Direction: `S86-51-49W`<br>
    Building 17 & 15 NE Direction: `N2-54-55E`,
    SW Direction: `S2-03-16W`<br>
    Custis Ct Buildings NE Direction: `N85-28-39E`,
    SW Direction: `S86-08-36W`<br>
  </sub></sub>
<br>
<b>3-</b> Draw lines <br>
    Edit Tab > Create > Click point for point one of line, right click Direction and Distance, type in Direction and Distance
<sub><sub>
    Notes My Settings:
    2 stories Distance = 15ft
    3 Stories Distance = 20ft
    4 Stories Distance = 25ft.
</sub></sub>
<br>
<b>4-</b> Add Address points <br>
http://pro.arcgis.com/en/pro-app/help/editing/create-point-features-along-a-line.htm <br>
    Edit Tab > Create > Click Secondary Address >Click Points Along a Line> For each line of Row of addresses, Select Line > Check mark Additional Points At start of line and at end of line<br>
  <sub>
    For Three Stories: > Number of Points = 1> Click Create <br>
    For Four Stories: > Number of Points = 2> Click Create <br>
  </sub>
<br>
<b>5-</b> Select > Click on building point > Right Click Attributes > Attributes Window > Right Click > Copy Attributes <br>
<br>
<b>6-</b> Select > Draw a square around the address points for that building <br>
<br>
<b>7-</b> Attributes > Right Click Address > Paste Attributes <br>
<br>
<b>8-</b> For each address point add the Unit Number in the Street Number Field. <br>
<br>
<b>Alternative Method:</b> http://support.esri.com/en/technical-article/000012318<br>
<b>9-</b> Synchronize Edits to File Geodatabase <br>
    As of September 2017 you still have to use <b>ArcMap</b> to have access to necessary Distributed Geodatabase Tools. Can't manage and synchronize replicas in ArcGIS Pro. No overall advantage to editing in ArcGIS Pro VS ArcMap when the final steps have to be preformed in ArcMap anyway. <br>
<br>
Distributed Geodatabase Tools ArcMap: <img src="https://github.com/akell47/GIS/blob/master/GISImages/DistributedGeodatabaseToolsArcMap.JPG"
    width="250" height="200"/><br>
Distributed Geodatabase Tools ArcPro: <img src="https://github.com/akell47/GIS/blob/master/GISImages/DistributedGeodatabaseToolsArcPro.JPG"
        width="200" height="100"/> <br>
<br>
Handy Distributed Geodatabase Toolbar in ArcMap: <img src="https://github.com/akell47/GIS/blob/master/GISImages/SynchronizeChangesWizard.JPG"
        width="250" height="250"/>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/Synchronizing.JPG"
        width="220" height="200"/>
<br>
<br>
### Video
https://youtu.be/r2u0-0Y2kPA

## Before
<img src="https://github.com/akell47/GIS/blob/master/GISImages/before_addAddresses.JPG"
width="550" height="400"/> <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/Before_addAddresses_SM.JPG"
width="600" height="500"/> <br>
## After
<b>Parallel Evenly Spaced Points</b><br>
<br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/After_addAddresses.JPG"
width="550" height="400"/> <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/After_addAddresses_SM.JPG"
width="600" height="500"/> <br>
