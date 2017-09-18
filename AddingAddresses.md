We have an apartment complex and need to add addresses to them. The private roads within the apartment complex are private roads. We have addresses of the buildings but we are missing the unit numbers. The unit numbers are part of the street number of the address.  Unit 1535, is `1535 [Street Name].`
## Tools:
ArcGIS Pro.
Existing project opened into ArcGIS Pro project environment

## Execution:
1- Import mxd into Pro. <br>
Add address points <br>
1- Create line feature for points to be added upon. <br>
    Open Create Feature Class Tool > New Line Template in Layers <br>
2- Determine QB Direction to make all lines parallel
    Start to draw the line, move mouse out to desired looing angle. Don't finish the line, instead right click > Direction > Copy Direction. <br>
    http://pro.arcgis.com/en/pro-app/help/editing/direction-formats-for-editing.htm <br>
    http://pro.arcgis.com/en/pro-app/help/editing/specify-a-direction-and-distance.htm <br>
    East Direction: `N90-00-00E`<br>
    West Direction: `S90-00-00W`<br>
    North Direction: `N0-00-00E`<br>
    South Direction: `S0-00-00W`<br>
    Building 8 Slight NE Direction: `N3-32-22W`<br>
    Building 8 Slight SE Direction: `S4-17-21E`<br>
    Building 12 SW Direction: `S63-48-43W`<br>
    Building 12 NE Direction: `N64-03-28E`<br>
    Potomac Buildings SE Direction: `S3-40-04E`
    Potomac Buildings NW Direction: `N4-30-50W`
3- Draw lines <br>
    Edit Tab > Create > Click point for point one of line, right click Direction and Distance, type in Direction and Distance (Distance = 20ft). <br>
4- Add Address points <br>
    Edit Tab > Create > Click Secondary Address >Click Points Along a Line> For each line of Row of addresses, Select Line > Check mark Additional Points At start of line and <br>
    For Three Stories: Check mark At end of line. > Number of Points = 1. Click Create <br>
    For Four Stories: Check mark At end of line. > Number of Points = 2. Click Create <br>
5- Select > Click on building point > Right Click Attributes > Attributes Window > Right Click > Copy Attributes <br>
6- Select > Draw a square around the address points for that building <br>
7- Attributes > Right Click Address > Paste Attributes <br>
8- For each address point add the Unit Number in the Street Number Field. <br>
<br>

### Video
https://youtu.be/r2u0-0Y2kPA

## Before
<img src="https://github.com/akell47/GIS/blob/master/GISimages/before_addAddresses.JPG"
width="400" height="400"/> <br>
<img src="https://github.com/akell47/GIS/blob/master/GISimages/Before_addAddresses_SM.JPG"
width="400" height="400"/> <br>
## After
<img src="https://github.com/akell47/GIS/blob/master/GISimages/After_addAddresses.JPG"
width="400" height="400"/> <br>
