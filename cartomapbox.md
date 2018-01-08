## Creating Simple webmap (points) using MapBox basemap and Carto
This tutorial shows you how to use mapbox basemap and carto to make a simple webmap without coding.
### Geocoding
Geocoding typically refers to taking some sort of list of addresses and returning X (|||longitude|||) and Y (---latitude---) information. Mapbox requires latitude and longitude information for datasets.
First thing we are going to do is set up a spreadsheet of the location you want to map and save it as a `.csv` file.
For US addresses ideally best practices are a field for:
- index
- Street Address ([number] [full street name])
- City
- State
- Zip Code
- And another single field of all the above <br>
Best practices include:
- The fields should have header names and with no spaces
- letters and numbers only
- should not start with a number.
I'm going to use a geocoding service called geocodio https://geocod.io/ Texas A&M has a geocoding service (for USA locations) and a great list of other geocoding services including international options. https://geoservices.tamu.edu/Services/Geocode/OtherGeocoders/ <br>
#### Geocodio
I'm going to use a geocoding service called geocodio https://geocod.io/
geocodio needs the fleids to be as
```
id,	name,	address,	zip_code,	city,	state
```
*And nothing else.* Get the X and Ys and then put them back into another spreadsheet with webpage links that you will use in carto.

### Mapbox
Create an account. <br>
Now that you have latitude and longitude, create a new csv file with a field for `labels` that you want to display in the basemap. Click on your profile and go to *Studio*. Go to the datasets tab to upload the geocoded addresses. Give the dataset a name then it will open into a map then you click import to upload your data. Then just click the button to go back to home.  You do not need to upload a dataset to mapbox to use their basemap, but it adds additional customization options to the points we want to display in the final map.<b> Adding dataset to mapbox is totally optional at this point you can just slect your style and that is it</b><br>
Within your "studio" click on the home tab, then scroll down under the heading "Get Started" and click "Explore Styles."  (North Star is my favorite.) Click "Add this style."  The style you select is now in your profile under the "styles" tab. <b>You can stop here rest is optional/ not necessary </b> <br>
To add the points from your dataset click on the button `+Layer` Then click "No tileset, click to select" then click "New Tileset" then "Create from dataset" and "Export." The layer will not appear - now you have to go back to "tilesets" under the Studio tab and click on the stacked lines next to Menu and click "Add tileset to style" Click the style (map) want to add your points to. <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/mapboxdataset.JPG" width="1000" height="550"/> <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/adddatatomap.JPG" width="1000" height="300"/> <br>
Your map should open back up but if not go back to your *styles* tab and then click on your style (map). The map background will look weird, click add layer. You will now see your points and can style the points. <br>
<b> Labels *Optional* </b> <br>
Now we are going to use our dataset to add labels.  Change the dataset from circle to tet by selecting your new dataset, click "Select Data" and change type to "T Symbol." <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/mapboxlabel.JPG" width="450" height="400"/> <br>
Click on "Style" set Text field value to your column with labels. <br><br>
Alternatively you can add labels in carto instead. The benefit of adding your labels in MapBox instead of carto is that the basemap labels will move out of the way/ not interfere with your data's labels. The disadvantage is that the icons in carto will overlap and be on top of your mapbox labels.

### Carto
Set up your spreadsheet you will use in carto for pop-ups. If you know you want to have links go ahead and make one as a regular URL another one as a HTML link `<a href="URL%link.com">Link Label</a>`- just in case one works better than the other. <br>
In carto navigate to your "dashboard" then you navigate from maps and datasets by clicking the dropdown next to your profile name. <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/carto_navigate.JPG" width="450" height="200"/> <br>
Click on "New Dataset" it will upload then you will see your data then click "Create Map"
 <br>
<b> basemap </b><br>
Now we are going to bring in the mapbox basemap.  Click on basemaps then scroll through the basemaps in Source and click on "MAPBOX" Then under Style click the + for Add. You will then be asked for your Map ID and Access Token. To find this go back to your mapbox styles.  In the style you created above click the stacked lines next to Menu - click "Share, develop & use" <br>
Copy the Integration URL <img src="https://github.com/akell47/GIS/blob/master/GISImages/mapboxintegrateurl.JPG" width="400" height="300"/> <br>
Paste that into the box in carto for Map ID/URL.  Within that URL find the part after `access_token=` copy and paste that into the Access Token box. Then click ADD BASEMAP. <br>
The mapbox basemap should now be in your carto map. <br>
<b> icon </b><br>
Now click on your dataset and we are going to change the icon. Under Style click the color in SIZE/COLOR then click "IMG" then click "Show full collections." <br>
<img src="https://github.com/akell47/GIS/blob/master/GISImages/mapbox_changeicon.JPG" width="600" height="400"/> <br>
Now you should see a bunch of icons and click "UPLOAD FILE." https://gis.stackexchange.com/questions/132276/how-to-use-custom-marker-symbols-in-cartodb <br>
This is supposed to work but the PNG and the SVG image I am uploading is not working... <br>
<b>Pop-up</b><br>
Click on "POP-UP" to customize the point pop-up. Select which fields you want to show up.  The HTML link works better than the plain URL.  
<b>Share</b><br>
Click "Publish" to share. Cick "Publish" again then the map will change to "Public" and links will show up under "Get the link" and "Embed It." Click on "Embed It" to get the iframe code to drop into your website.
