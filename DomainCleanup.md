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
(You don't have to use jupyter notebook) <br>
### Listing out the Domains
<b> All the Domains </b> http://desktop.arcgis.com/en/arcmap/10.3/analyze/arcpy-data-access/listdomains.htm <br>
For the part of the code sample which is the file path, `domains = arcpy.da.ListDomains("C:/Boston/Boston.gdb")` You can find the file path to your geodatabase in ArcCatalog right click properties on the .gdb and copy/paste the file path in the Name under the general tab. In python you need to then change the slashes in the filepath to forward slashes or double up the back slashes. <br>
For the rest of the code, in the code sample in the link, just copy paste! This will give you a lit of each domain and the coded values. <br>
For a simple plain list, simply use:
```
for domain in domains:
    print(domain.name)
```

<b> Domains in Use </b> https://gis.stackexchange.com/questions/9981/listing-feature-classes-with-active-domains <br><br>
I want to return a list so that I can convert the list into a Pandas Data Frame object. To change the output into a list object you append the output to an empty list `[]` <br>
<b>Domains in Use</b>
```
#Get list of feature classes in geodatabase
def DomainsinUse():
    domainList = []
    FCs = arcpy.ListFeatureClasses()
#Loop through feature classes in list
    for FC in FCs:
    #List fields in feature class
        fields = arcpy.ListFields(FC)
    #Loop through fields
        for field in fields:
        #Check if field has domain
            if field.domain != "":
            #domain name
                domainList.append(field.domain)
    return domainList

print (DomainsinUse())
```
<b> All the Domains </b>
```
def allDomains():
    all_Domains = []
    for domain in domains:
        all_Domains.append(domain.name)
    return all_Domains
print (allDomains())
```
### Pandas DataFrame
For each list of Domains, (Domains in Use, Domains Not in Use) turn into a Pandas DataFrame. <br>
<b>Domains In Use</b>
```
inUse = DomainsinUse()
dfInUse = pd.DataFrame(inUse)
dfInUse
```
If you have any domains used more than once you will have duplicate values. Remove the duplicate values with `drop_dupicates`. Also give the column header a name ('Domains').
```
pd.DataFrame.drop_duplicates(dfInUse, inplace=True)
dfInUse.columns = ['Domains']
dfInUse
```
<b>All the Domains</b> with column name
```
alltheDomains = allDomains()
dfAll = pd.DataFrame(alltheDomains)
dfAll.columns = ['Domains']
dfAll
```
### Compare the two Lists
First just to get a count of each list you can use `range(len(df_Name))` <br>
Now to compare the two lists (`import numpy as np`) https://stackoverflow.com/questions/29780788/python-pandas-what-is-the-most-efficient-way-to-compare-two-lists-in-a-loop <br>
```
dfAll['toRemove'] = np.where(dfAll['Domains'].isin(dfInUse['Domains']), 'InUse', 'Not in Use')
dfAll
```
Now we have a list of Domains that are currently in use and not in use!!! <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/DomainUseList.JPG"
        width="425" height="393"/> <br>
