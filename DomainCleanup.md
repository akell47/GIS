## Clean up Domains in Geodatabase.
Overtime you might end up with a bunch of domains in your geodatabase and would like to clean them up. How do you know which ones to delete and which ones are in use. Maybe you just would even like to see the domains listed out.
Going to use juypyter notebook with Esri. In order to use arcpy in jupyter notebook you have to the hardest step of the process, launching jupyter notebook from the ArcGIS pro command line space. This is located at: <br>
`C:\Program Files\ArcGIS\Pro\bin\Python\Scripts\proenv.bat` <br>
Right click `proenv.bat` and click run as administrator.
Navigate back to `C:\Program Files\ArcGIS\Pro\bin\Python\Scripts\proenv.bat` in the command line, then type `jupyter notebook` <br>
If jupyter notebook doesn't launch automatically copy and paste the login token into your preferred browser <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/launchjupyterarcgis.JPG"
        width="490" height="330"/> <br>
Create a new notebook and `import arcpy` <br>
You don't have to use jupyter notebook, you can use regular command line. <br>
### Listing out the Domains
http://desktop.arcgis.com/en/arcmap/10.3/analyze/arcpy-data-access/listdomains.htm
for the part of the code sample which is the file path, `domains = arcpy.da.ListDomains("C:/Boston/Boston.gdb")` You can find the file path to your geodatabase in ArcCatalog right click properties on the .gdb and copy/paste the file path in the Name under the general tab. In python you need to then change the slashes in the filepath to forward slashes or double up the back slashes. <br>
For the rest of the code, in the code sample, just copy paste! This will give you a lit of each domain and the coded values. <br>
For a simple plain list, simply use:
```
for domain in domains:
    print(domain.name)
```

### List out Feature Classes with Active domains
https://gis.stackexchange.com/questions/9981/listing-feature-classes-with-active-domains
