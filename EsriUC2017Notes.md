## Model Builder Introduction
Model Builder Tab > Tools - Geoprocessing Pane <br>
Store bin of your work and workflows <br>
Visual programming language <br>
Drop shadows - model worked <br>
right click - add to display to see results <br>
run within modelbuilder or save in toolbox and run from tool dialogue <br>
Model Parameter - add output to display <br>
Rename tools to make sense to others <br>
Tool Properties - change order sequence <br>
Iterators - loop over data <br>
Utility tools - Collect Values - add to display - remove output option - just modify data <br>
Model Parameters - Symbology options <br>
Group - Select and group sections - name it - expand and collapse with grouping <br>
check relative path - to make a relative path <br>
Environments - set workspace - %scratchworkspace%\restofpath <br>
Nesting - model within a model <br>
<br>
## Python: Introduction to Map Automation
Jeff Barrette <br>
ArcPy <br>
manage MXDs/projects, layer files, and contents <br>
find layer with data source and replace data sourceupdate Symbologygenerate reports lists doc info like data sources, broken layers, spatial reference etc <br>
Automate exporting and printing <br>
arcpy.mp - mapping module <br>
check out arcpy.mp help and tutorial
http://pro.arcgis.com/en/pro-app/arcpy/mapping/introduction-to-arcpy-mp.htm
python window <br>
ArcGISProject function - commands that do things <br>
class - objects that do things <br>
`ArcGISProject(aprx_path)` <br>
takes a path to an aprx file on disk or special keyword "CURRENT" <br>
Reference project on disk <br>
`aprx = arcpy.mp.ArcGISProject(r"C:\path\some.aprx)` <br>
`lyt = aprx.listLayouts('Layout')[0]` <br>
`lyt.exportToPDF(r"C:\Temp\Ooutput.pdf)` <br>
Can run externally - must import arcpy module ` import arcpy` <br>
`p = arcpy.mp.ArcGISProject('current')` <br>
`p.` see properties and methods <br>
`p.filepath` <br>
`p.importDocumentr"C:\path.mxd` <br>
`p.saveACopy(r"C:\filepaht.aprx)` <br>
aprx - Pro's version of mxd - can import mxd not export to mxd <br>
Use "List" functions on appropriate objects <br>
`mp = aprx.listMaps("parc*")[0]` <br>
`lyr = mp.listLayers()[0]` <br>
<b> [0] </b> remember the `[0]`!! <br>
list by index number first item always 0 <br>
Common Properties:
-Layers - definition Query, saveACopy, visible <br>
-Map - AddLayer, ClearSelection, defaultCamera <br>
`m = p.listMaps('Main Map')[0]` wild card <br>
`print(len(m.listBrokenDataSources()))` <br>
`lyrFile = arcpy.mp.LayerFile(r"C:\path\path.lyrx")` adds a layer to the Map <br>
`lyr = m.listLayers('GreatLakes')[0]` <br>
`lyr.visible = False` <br>
`lyt = p.listLayouts()[0]` <br>
`txt = lyt.listElements('TEXT_ELEMENT', "Title")[0]` <br>
`txt.text = "new Title Name"` <br>
`pic = list.listElements('PICTURE_ELEMENT')[0]` <br>
`pic.sourceImage = r"C:\file\path\pic.jpg` <br>
`mf = lyt.listElements('MAPFRAME_ELEMENT', 'Main*')[0]` <br>
`bk = m.listBookmarks('Lake Huron')[0]` <br>
`mf.zoomToBookmark(bk)` <br>
`selExt = mf.getLayerExtent(lyr, True)` <br>
`selExt = arcpy.SelectLayerByAttribute_management(lyr, 'NEW_SELECTION',  "NAME = 'LakeHuron'"")` <br>
`mf.camera.setExtent(selExt)` <br>
`lyt.exportToPDF(r"C:\file\path\map.pdf)` <br>
append PDFs <br>
`myPDF = arcpy.md.PDFDocumentCreate(r"C:\file\path\newmap.pdf)` <br>
`myPDF.appendPages(r"C\file\path\Append_map.pdf)` <br>
creates pdf in memory and appends to it. <br>
<b>esriurl.com/8899 <br>
esriurl.com/9785 </b>

#### Part 2
Jeff Barrette & Jeff Moulds <br>
Can add dynamic tables with Python - unavailable otherwise currently <br>
Report Lab - pdf authoring tool <br>
ArcPro - Map, Map Frame, Camera (3D extent), multi-page layouts <br>
http://pro.arcgis.com/en/pro-app/arcpy/mapping/migratingfrom10xarcpymapping.htm <br>
```
import arcpy, os
folder = r"C:\FileFolder"
for file in [f for f in os.listdir(os.path.join(folder, 'MXDs'))
            if os.path.splittext(f[1].lower() == '.mxd')]:
```
`aprx.importDocument(r"C:\Project\file\path\map.mxd", include_layout=True)`
.mapx file - like a layer file - way to share maps across users <br>
.pagx file - for layout template <br>
Updating data sources
```
aprx = arcpy.mp.ArcGISProject(r'C:\File\Path\map.aprx`)
aprx.updateConnectionProperties(r'C:\File\Path\layer.gdb,
                    r'C:\File\Path\server.sde`)
```
Changing a folder
```
aprx = arcpy.mp.ArcGISProject(r'C:\File\Path\layer.aprx')
aprx.updateConnectionProperties('DataFolder', 'NewDataFolder')
```
Changing Layer files
```
lyrx = arcpy.mp.LayerFile(r'C:\Filepath\layer.lyrx')
lyrx.updateConnectionProperties('DataFolder', 'NewDataFolder')
```

`aprx.updateConnectionProperties('PFDB.mdb', 'FGDB.gdb', auto_update_joins_and_relates=True)`<br>
<br>
New with Pro - the entire layer data source object model is exposed as a Python dictionary.
```
import arcpy, pprint
<br>
http://pro.arcgis.com/en/pro-app/arcpy/mapping/updatingandfixingdatasources.htm
<
