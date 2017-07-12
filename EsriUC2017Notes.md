## Model Builder Introduction
Model Builder Tab > Tools - Geoprocessing Pane
Store bin of your work and workflows
Visual programming language
Drop shadows - model worked
right click - add to display to see results
run within modelbuilder or save in toolbox and run from tool dialogue
Model Parameter - add output to display
Rename tools to make sense to others
Tool Properties - change order sequence
Iterators - loop over data
Utility tools - Collect Values - add to display - remove output option - just modify data
Model Parameters - Symbology options
Group - Select and group sections - name it - expand and collapse with grouping
check relative path - to make a relative path
Environments - set workspace - %scratchworkspace%\restofpath
Nesting - model within a model

## Python: Introduction to Map Automation
Jeff Barrette
ArcPy
manage MXDs/projects, layer files, and contents
find layer with data source and replace data sourceupdate Symbologygenerate reports lists doc info like data sources, broken layers, spatial reference etc
Automate exporting and printing
arcpy.mp - mapping module
check out arcpy.mp help and tutorial
http://pro.arcgis.com/en/pro-app/arcpy/mapping/introduction-to-arcpy-mp.htm
python window
ArcGISProject function - commands that do things
class - objects that do things
`ArcGISProject(aprx_path)`
takes a path to an aprx file on disk or special keyword "CURRENT"
Reference project on disk
`aprx = arcpy.mp.ArcGISProject(r"C:\path\some.aprx)`
`lyt = aprx.listLayouts('Layout')[0]`
`lyt.exportToPDF(r"C:\Temp\Ooutput.pdf)`
Can run externally - must import arcpy module ` import arcpy`
`p = arcpy.mp.ArcGISProject('current')`
`p.` see properties and methods
`p.filepath`
`p.importDocumentr"C:\path.mxd`
`p.saveACopy(r"C:\filepaht.aprx)`
aprx - Pro's version of mxd - can import mxd not export to mxd
Use "List" functions on appropriate objects
`mp = aprx.listMaps("parc*")[0]`
`lyr = mp.listLayers()[0]`
<b> [0] </b> remember the `[0]`!!
list by index number first item always 0
Common Properties:
- Layers - definition Query, saveACopy, visible
- Map - AddLayer, ClearSelection, defaultCamera
`m = p.listMaps('Main Map')[0]` wild card
`print(len(m.listBrokenDataSources()))`
`lyrFile = arcpy.mp.LayerFile(r"C:\path\path.lyrx")` adds a layer to the Map
`lyr = m.listLayers('GreatLakes')[0]`
`lyr.visible = False`
`lyt = p.listLayouts()[0]`
`txt = lyt.listElements('TEXT_ELEMENT', "Title")[0]`
`txt.text = "new Title Name"`
`pic = list.listElements('PICTURE_ELEMENT')[0]`
`pic.sourceImage = r"C:\file\path\pic.jpg`
`mf = lyt.listElements('MAPFRAME_ELEMENT', 'Main*')[0]`
`bk = m.listBookmarks('Lake Huron')[0]`
`mf.zoomToBookmark(bk)`
`selExt = mf.getLayerExtent(lyr, True)`
`selExt = arcpy.SelectLayerByAttribute_management(lyr, 'NEW_SELECTION', "NAME = 'LakeHuron'"")`
`mf.camera.setExtent(selExt)`
`lyt.exportToPDF(r"C:\file\path\map.pdf)`
append PDFs
`myPDF = arcpy.md.PDFDocumentCreate(r"C:\file\path\newmap.pdf)`
`myPDF.appendPages(r"C\file\path\Append_map.pdf)`
creates pdf in memory and appends to it.
esriurl.com\8899
