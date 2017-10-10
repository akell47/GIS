## Creating Simple Network Dataset and Network Analysis

### Requirements
ArcMap and Network Analysis Extension <br>
streets layer

### Network Analysis Parameters
- Calculate distance field
- Private roads category
- Walk time / drive time
- Hierarchy Class

#### Resources
http://downloads.esri.com/support/whitepapers/other_/ArcGIS_NA_Hierarchical_Routes_Aug05.pdf<br>
http://desktop.arcgis.com/en/arcmap/latest/extensions/network-analyst/network-analysis-with-hierarchy.htm<br>
Good one!->http://www.gsf.ca/getattachment/50e5680c-f73d-4ba9-a5b2-7bbac131e396/ArcGIS_Desktop_Network_Analyst_White_Paper_Preparing_Street_Data.pdf.aspx<br>
http://desktop.arcgis.com/en/arcmap/latest/extensions/network-analyst/editing-network-datasets-modifying-network-attributes.htm<br>
http://desktop.arcgis.com/en/arcmap/latest/extensions/network-analyst/types-of-evaluators-used-by-a-network.htm<br>
<br><br>

#### Prep Data
Open ArcMap <br>
Seems like you must prep data before creating the Network Dataset.  Within SDE geodatabase Feature Dataset cannot Register data as versioned (Right click Feature Dataset> Manage > Register as Versioned) once network dataset is created in the Feature Dataset.  If you have a Network Dataset already built you have to delete Network Dataset then add / edit fields.
<br><br>
<b>Distance Field</b><br>
Add Field > Miles, type: Double. Start edit session. Right click field Calculate Geometry.<br>
Property: Length, Units: Miles
<br><br>
<b>Private Roads</b><br>
Stop Edit Session. Add Field > IsPrivate, type: Text, Length: 1. Start edit session. Select private roads, Right click IsPrivate field > Field Calculator > `IsPrivate = "Y"` > Click Switch Selection > Field Calculator > `IsPrivate = "N"`.
<br><br>
<b>Walk time</b><br>
`minutes = Miles / [speed]` speed is in miles per hour. If you have a Feet Field. Using average walk speed of 3.1 miles per hour. `Walk time in minutes  = ([Miles] / 3.1) * 60` <br>
Stop Edit Session. Add Field > walkMinutes, type Double. Start edit session. Right click field > Field Calculator > `walkMinutes = ([Miles] / 3.1) * 60`
<br><br>
<b>Hierarchy Class</b>
Categorize Roads Ordinally as 1,2,3.  Primary Roads lower numbers (1 highest level), Secondary Roads, middle number (2 middle level), and Local Roads highest number (3 lowest level).
Stop Edit Session, Add Field > Func_Class type: Short Integer. Start edit session. Field Calculator 1,2,3 roads accordingly.<br>
Close ArcMap<br>

#### Build Network Dataset
Open ArcCatalog.<br>
Streets layer must be part of a Feature Dataset. Right click Feature Dataset > New > Network Dataset <br>
Under the Attributes Tab of the Network Dataset wizard add a parameter Click Add... type the field name exactly the same as the field name. Once added click Evaluators...> In the Evaluators window change Type to Field. Click the little hand button under the "X".  Set Field Evaluator in the Code block.<br>
Pre-Logic Script Code:
```
def AvoidPrivate():
    output=False
    if [isPrivate]("Y")==True:
        output=True
    return output
```
```
def AvoidPrivate():
    if !IsPrivate!=='Y':
        return True
    else:
        return False
```
Call the function in the box Value = `AvoidePrivate()`<br><br>
<img src="https://github.com/akell47/GIS/blob/master/NetworkAnalysis/images/AvoidPrivate.JPG"
width="700" height="430"/><br>
<br>
Add walkMinutes, Usage Type: Cost, Units: minutes<br>
<br>
Add Func_Class, Usage Type: Hierarchy <br>
<br>
Under Travel Modes Tab > Travel Mode: add "walk", Type: Walk, Impedance: Miles (Miles), Time Attribute: walkMinutes (Minutes), U-Turns at Junctions: Allowed, Use Hierarchy: uncheck, Restrictions: check IsPrivate <br>
Close ArcCatalog <br>
#### Network Analysis

Going to create a half-mile walking distance around Marta Bus stops, Libraries, and Parks <br>
Open ArcMap <br>
Make sure Network Analyst extension is check marked. Customize > Extensions <br>
From Catalog tree, drag and drop Network Dataset into the map > Click Yes for Do you also want to add all feature classes that participate in Street_ND to the map. <br>
Open Network Analyst toolbar > Network Analyst Drop Down > Click New Service Area > Click the icon with the square and the flag. <br>
Before you Load Locations, Click the little square button in the upper right corner of the Network Analyst window to open the Layer Properties window.  Under the Network Locations tab set the Name Property so when you Load Locations they will have names that make sense. Under Candidate Fields type the field name you want to label the locations with. <br>
Load Facilities for Service Area > Right Click Facilities (0) > Load Locations> Load From: Select Layer The name should show up under Field.  <br>
