---
description: Written by Tomoko Acoba and Melanie Abecassis
---

# ArcGIS tutorial



This tutorial will teach you how to import NetCDF data into ArcGIS, extract environmental values at survey locations, or within polygons. Finally, you'll learn how to create a habitat map based on a range of SST values.

You will need the **spatial analyst** extension to complete this tutorial.

## Introduction

Esri’s ArcMap is a program with an intuitive graphic user interface. Once you are familiar with the general structure of the program, it is easy to navigate. The trade-off is that it can be very slow. Please be aware that you might need patience if working with large datasets.

In Esri’s world, data with x \(long\), y \(lat\) and time dimensions, like ocean satellite data, are called **multi-dimensional data**.   
  
ArcMap wasn't originally designed to work with multi-dimensional data. Depending on how the data is configured, some functions may or may not be available and processing of the data may take a long time. \(R is a great alternative for large datasets!\)

Before starting the tutorial:

* Open an empty ArcMap, in the Catalog window, click on the “Connect to Folder” button, and make the connection to your working folder
* In ArcMap, click on “Customize” in the top menu, and “Extensions...”, and make sure the “Spatial Analyst” extension is checked.

## 1. General Navigation of ArcMap

![](../../.gitbook/assets/image%20%28247%29.png)

### General Navigation: Tools toolbar

![](../../.gitbook/assets/image%20%28238%29.png)

Mousing over individual icons displays descriptions of each tool. Greyed-out tools are not available to use.

## 2. Download NetCDF data from ERDDAP

Let's download some monthly SST data to work with.

Go to:  
[https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW\_sst\_v1\_0\_monthly.html](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW_sst_v1_0_monthly.html)

Make sure to select a reasonable subset in time and space \(see example below\). The amount of data that can be directly downloaded from ERDDAP is limited. Downloading a reasonable amount of data will also help the processing time in ArcGIS.   
Because of the download and processing limits, it is not recommended to work with a long time-series in ArcGIS \(for example, 365 days of daily chl-a, or 20 years of monthly composite of sst\).

Change the File type to “.nc – Download a NetCDF-3 binary file with COARD/CF/ACDD metadata”.

Once the settings are entered, click on the Submit button to download. 

Save the downloaded file on your computer.

![](../../.gitbook/assets/image%20%28194%29.png)

## 3. Import data into ArcGIS Desktop

* In the ArcMap’s Search Window \(top right side of the screen\), type in “Make NetCDF Raster Layer”. 
* Click on “Make NetCDF Raster Layer \(Multidimension\)” in the list to open the tool dialog box.
* Browse to the downloaded NetCDF file, and click “Open” to select the file as Input netCDF File. Notice that Variable, X Dimension, Y Dimension are automatically filled out.
* Keep Output Raster Layer as analysed\_sst\_Layer. 
* Click OK

![](../../.gitbook/assets/image%20%28265%29.png)

![](../../.gitbook/assets/image%20%28272%29.png)

## 4. Enable the Time Slider

* In the table of contents, right click analysed\_sst\_Layer, and then click on “Properties”.
* Under the Time tab of the Properties window, check “Enable time on this layer”.
* Change the Time dimension to time.
* Change the Time Step Interval to an appropriate interval. Since this example is a monthly composite, change it to 1.00 Months.
* Click OK

![](../../.gitbook/assets/image%20%28280%29.png)

* In the Tools toolbar, click on the Time Slider button:

![](../../.gitbook/assets/image%20%28286%29.png)

* In the Time Slider window, click the play button to see the changes of SST over time:

![](../../.gitbook/assets/image%20%28237%29.png)

If it plays too fast or too slow, click on the Options button, and under the Playback tab of the Time Slider Options, adjust the playing speed.   
  
You can also export the animation as a movie file \(using the “export to video” button\), however the quality of the movie is dependent on the size of the data and the graphics card of the computer.

## 5. Create a map

You will need to download the [esd\_fish\_survey\_2016.csv](http://oceanwatch.pifsc.noaa.gov/files/esd_fish_survey_2016.csv) file and save to your working folder.

* If the analysed\_sst\_Layer is still playing, click the Pause button.  You can adjust the time to a month of particular interest for which you want to create a map
* In the Catalog window, navigate to your working folder on your desktop. 
* Drag and drop the “esd\_fish\_survey\_2016.csv” file into the map
* Right-click the added table in the table of contents, and click “Display XY Data”... 
* In the “Display XY Data” window, choose LONGITUDE as X Field, and LATITUDE as Y Field. 
*  Click on the “Edit...” button to choose WGS 1984 coordinate system by expanding Geographic Coordinate Systems Folder&gt; World&gt; WGS 1984 and click OK

![](../../.gitbook/assets/image%20%28257%29.png)

* Click OK to the message “Table Does Not Have Object-ID Field”
* The layer added is a temporary layer from the table.  To make it permanent, you will have to export it as a shapefile by right-clicking the esd\_fish\_survey\_2016.csv Events layer and then Data &gt; Export Data... 
* Browse to the ArcGIS\_PIFSC\_demo folder, select type “shapefile” and save it as esd\_fish\_survey\_2016\_export.shp 
* Right-click the exported shapefile, and click “Zoom to Layer”

**If you already know how to create a map in ArcMap, you can skip this part of the tutorial.** 

* On the top menu, click View &gt; Layout View  Layout view will allow you to create a map with your data, and insert map elements like a North Arrow, a Legend, and a Scale Bar 
* On the top menu, click Insert &gt; Legend 
* In the Legend Wizard window, click through Next to accept all the default settings and click Finish to generate the Legend 
* To change the descriptions on the legend, you will have to change them in the table of contents. 
* Right click the exported shapefile, click on Properties, change the name to 2016 Fish Survey Sites under the “General” tab, and click OK. 
* Follow the same steps for anlysed\_sst\_Layer, and change the name to SST
* Right-click the legend on the map, and click on Properties. Under the “General” tab, delete Legend, under the “Frame” tab, change the background to white, and click OK 
* From the top menu, insert a North Arrow of your choice, and a scale bar. 
* To change the unit of the scale bar, right click the scale bar, and click on Properties. Under the Scale and Units bar, change the division units to Kilometers 

The map should look like this:

![](../../.gitbook/assets/image%20%28263%29.png)

* You can export the map as a PDF by clicking "File" in the top menu and "Export Map". 
* Choose PDF for “Save as type” and save the map on your computer. 
* To save the map you created, click on the Save button \(floppy disk button\) and save the project as “sst\_netcdf\_map.mxd” on your computer.

Since the longitude range in the NetCDF file is from 0 to 360 degree, the SST data may not align with the fish survey data. There are a couple of ways to fix this issue...   
The easiest way is to change the projection of the map document to your data, instead of changing the NetCDF data.   
In the Table of Contents, click on Layers \(on the very top\), and click on Properties. Under the Coordinate System tab, expand Layers folder, and GCS\_WGS\_1984. Select your data under GCS\_WGS\_1984, and click OK.

![](../../.gitbook/assets/image%20%28201%29.png)

## 6. Extract SST values at survey points

* If you are in the layout view, go back to the data view by clicking View on the top menu, and click on Data View 
* In the table of contents, right click on the SST layer, and click on Properties 
* Under the NetCDF tab, choose time for Band Dimension and click OK 
* In the Search window, search for the "Sample" tool 
* Click Sample \(Spatial Analyst\) tool and fill in the following parameters 
  * Input rasters: SST layer 
  * Input location raster or point features: 2016 Fish Survey Sites shapefile 
  * Output table: sample\_sst\_w\_fishsites\_new.dbf
  * Resampling technique: NEAREST 
  * Unique ID field: SITEVISITID 
* Click OK to run the tool, and once it is completed, click Close 
* Right click sample\_sst\_w\_fishsites\_new in the table of contents, and Open the table 
* Notice the column names don’t indicate the months, but it starts from the first month in the SST dataset to the last month.

## 7. Export the SST layer

The SST Layer is a temporary file, displayed from the NetCDF file.   
To make it permanent and make it easier to work with in ArcMap, the layer needs to be exported. 

* If you have not done so, in the table of contents, right click on the SST layer, and click on Properties. Under the NetCDF tab, choose time for Band Dimension and click OK to make sure that the different time steps will be exported properly.  \(Note: When this is done, the time slider won’t work properly anymore ….\) 
* Right-click on the SST layer, then click on Data and Export Data 
* Set the Location to your working folder. 
* Name it SST\_Layer1.tif, set the format to TIFF and click on “Save”. 
* Click Yes to add the exported data as a layer.

![](../../.gitbook/assets/image%20%28228%29.png)

If the new layer looks weird, with just red, blue, and green colors instead of a color scale, right-click on the layer, Properties, Symbology, then click on “Stretched” instead of “RGB Composite” in the list on the left and select an appropriate color scale \(You might need to click on “Invert” to make sure warm colors correspond to high values\).

## 8. Calculate statistics within polygons

Let’s calculate some summary statistics of SST within a shapefile.   
  
First, you will need to download the [Satellite toolbox](https://oceanwatch.pifsc.noaa.gov/files/Satellite.tbx) and the [3 nautical mile boundary shapefile](http://oceanwatch.pifsc.noaa.gov/files/3_naut_mile_bndry.zip). Save the files to your working directory, and unzip the shapefile.

The “Zonal statistics as table” tool from the Spatial Analyst extension allows users to calculate summary statistics from raster data over a specific zone \(a polygon or another raster\). However, it can only be run on one raster layer \(or raster band, i.e. time step in our case\) at a time.   
Some analyses may require running the tool multiple times. For this training, a custom model was built to run the tool on multiple raster bands \(i.e. time steps\) in one go. 

* In the Catalog window, navigate to your working folder, and drag the 3\_naut\_mile\_bndry\_wgs84.shp to the table of contents.  Using this shapefile, we will compute statistics of SST within the 3 nautical mile boundary, for each island. 
* To make sure the layers display properly, you can manually change the order of the layers.  Click the top left icon in the Table of Contents: “List by drawing order”. Then click-and-drag the 3\_naut\_mile\_bndry\_wgs84.shp layer above the chl-a layer in the Table of contents.

![](../../.gitbook/assets/image%20%28262%29.png)

* Right-click on the 3\_naut\_mile\_bndry\_wgs84.shp shapefile in the table of contents, and Open Attribute Table 
* Notice that there are 8 records, with each record corresponding to a polygon, for each island. 
* In the Catalog window, navigate to your working folder, and locate the toolbox Satellite.tbx

![](../../.gitbook/assets/image%20%28261%29.png)

* Expand the Satellite.tbx. 
* Double-click the “ZonalSt\_Merge” tool. 
* Enter the parameters as follows: 
  * Input Raster: SST\_Layer1.tif  **Note: make sure to browse to your working folder so that the path to the layer is entered**
  * Number of Bands: Up to 12  \(needs to match the number of bands, aka time steps, from the NetCDF file\) 
  * Zone Polygon: 3\_naut\_mile\_bndry\_wgs84.shp 
  * Zone Polygon Id: Island\_Name
  * Output Workspace: your working folder
* Click OK to run the tool 
* In working folder, find ZonalStatistics\_Output.dbf, drag and drop into ArcMap.  If you can not find the file in your catalog window, you might have to disconnect the folder \(right-click, “disconnect folder”\) and reconnect to it, or you can open the file in Excel instead. 
* Right-click the dbf file in the table of contents, and click Open 
* Note that the table is organized by island name and by Band \(i.e. month \# in our case\)

## 9. Suitability model – TurtleWatch

TurtleWatch is a tool developed by Dr. Evan Howell \(NOAA/PIFSC, Howell et al, 2008, 2015\) to advise longline fishermen on areas to avoid to reduce their likelihood to interact with loggerhead turtles which are a protected species. 

Every year, the Hawaii-based shallow-set longline fishery has a cap of interactions which triggers a fishery closure when it’s exceeded. For 2019, the cap was 17 interactions for loggerhead turtles. 

For loggerhead turtles, Howell et al 2008 showed that 50% of interactions have historically happened in waters with 17.5ºC &lt; SST &lt; 18.5ºC. 

Let’s create a map of the zone to avoid for a given day.

* Download SST data using the following link:  [https://oceanwatch.pifsc.noaa.gov/erddap/griddap/goes-poes-1d-ghrsst-RAN.nc?analysed\_sst\[\(last\)\]\[\(15\):1:\(45\)\]\[\(185\):1:\(235\)\]](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/goes-poes-1d-ghrsst-RAN.nc?analysed_sst[%28last%29][%2815%29:1:%2845%29][%28185%29:1:%28235%29]) This will download the latest SST data for the longline fishing ground.
* Start a new map in ArcMap.
* Use the “Make NetCDF Raster Layer” to import the data into ArcMap.  You’ll notice that the range of values is between 283 and 300. These are degrees Kelvin. We are going to need to convert these values to degrees Celsius. 
* In the search box, type “Raster Calculator” and open the tool.
* Drag your layer name in the middle box and type “- 273.15”. Click ok

![](../../.gitbook/assets/image%20%28255%29.png)

* In the search box, type “Reclassify” and open the “Reclassify \(Spatial Analyst\)” tool. 
* Select your new SST layer \(in ºC\) as the input layer and click on the “Classify…” button. 
* Change the number of classes to 3 and edit the 1st and 2d break values to 17.5 and 18.5 respectively and click OK.

![](../../.gitbook/assets/image%20%28273%29.png)

* On the first screen, change the new values to 0, 1, 0, then click ok.

![](../../.gitbook/assets/image%20%28183%29.png)

* Change the color for each class \(by right-clicking on each symbol\) to “No color” and dark red respectively. 
* Remove the layer in Kelvin, and change the color scale for the SST layer \(right-click, Properties, Symbology\). 

You now have a map of the zone to avoid. Add a graticule \(in Layout View, click on View, Data Frame Properties, Grids\), a legend and send it to your favorite longline fisherman!

![](../../.gitbook/assets/image%20%28268%29.png)

For more information on suitability modeling \(and on how to build more complex habitat models in ArcMap\), this free ESRI tutorial might also be of interest \(click on “Lessons and resources” to go straight to the tutorial about bob cat habitat suitability\): 

{% embed url="http://desktop.arcgis.com/en/analytics/case-studies/understanding-the-suitability-modeling-workflow.htm\#ESRI\_SECTION1\_7C9D35079E4A47929E6D53496D844769" %}







