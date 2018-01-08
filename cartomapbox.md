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
- And another single field of all the above
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
Now that you have latitude and longitude, create a new csv file with a field for `labels` that you want to display in the basemap. Click on your profile and go to *Studio*. Go to the datasets tab to upload the geocoded addresses. Give the dataset a name then it will open into a map then you click import to upload your data. Then just click the button to go back to home.  You do not need to upload a dataset to mapbox to use their basemap, but it adds additional customization options to the points we want to display in the final map.<br>
Within your "studio" click on the home tab, then scroll down under the heading "Get Started" and click "Explore Styles."  (North Star is my favorite.) Click "Add this style."  The style you select is now in your profile under the "styles" tab. <br>
To add the points from your dataset click on the button `+Layer` Then click "No tileset, click to select" then click "New Tileset" then "Create from dataset."
<img src="https://github.com/akell47/GIS/blob/master/GISImages/launchjupyterarcgis.JPG"
        width="1000" height="550"/> <br>
If you know you want to have links go ahead and make one as a regular URL another one as a HTML link `<ahref="URL%link.com">Link Label</a>`- just in case one works better than the other. <br>
