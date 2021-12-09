---
description: >-
  Written by Cara Wilson and Dale Robinson (CWWC). Adapted by Ron Vogel (CWEC)
  and Melanie Abecassis (OWCP)
---

# ERDDAP tutorial

This tutorial is also available as an audio-narrated [PowerPoint presentation](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/06-ERDDAP-intro.pptx).

**Objective:** \
\
Showcase the breadth of datasets available on various ERDDAPs and demonstrate how to graph and download data from ERDDAP.

## Familiarizing yourself with ERDDAP

ERDDAP was developed by Bob Simons from the NOAA SouthWest Fisheries Science Center.

ERDDAP is a platform to distribute data to users. Various institutions have installed ERDDAP to allow their users to visualize and download data.&#x20;

ERDDAP offers a consistent way to get data from a variety of different data sources. \
A variety of data types can be distributed on ERDDAP: in situ, satellite, or model data among others.&#x20;

ERDDAP lets you download data in your preferred data file format (netcdf, csv, ESRIcsv, JSON, ODVtext, mat, text and more).

ERDDAP lets you create images in your preferred image file format (png, transparent png, pdf, kml).&#x20;

It supports temporal and spatial subsetting.&#x20;

It is “RESTful”, meaning the URL completely defines the data you want, in the format you want. This means you can transfer the URL to another application and access the same data from there, for example, in your own webpage, or from your analysis software. You can even email the URL to a colleague and they can access the same data, image or plot that you generated.

&#x20;So ERDDAP works for both humans and machines!

## A short list of ERDDAP instances

* [CoastWatch West Coast ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap/index.html)&#x20;
* [OceanWatch Central Pacific ERDDAP](https://oceanwatch.pifsc.noaa.gov/erddap/index.html)&#x20;
* [CoastWatch Central ERDDAP](https://coastwatch.noaa.gov/erddap/index.html)
* [APDRC ERDDAP](https://apdrc.soest.hawaii.edu/erddap/index.html)&#x20;
* [PACIOOS ERDDAP](https://pae-paha.pacioos.hawaii.edu/erddap/index.html)

## Which ERDDAP should I use?

If you are unsure of which ERDDAP hosts the dataset you are interested in, you can use the following search engine, which compiles data hosted by 49 different ERDDAP instances across the world:\
[http://erddap.com/](http://erddap.com)

## Example #1. Examine the Kilauea algae bloom

![](<../.gitbook/assets/image (101).png>)

Following the 2018 lower Puna eruption, an algae bloom was observed off the east coast of the Big Island in June 2018 (visible near the easternmost point of the island if you zoom in).&#x20;

Let’s see what the chlorophyll concentration data looks like for that period.

* Go to the [OceanWatch ERDDAP](https://oceanwatch.pifsc.noaa.gov/erddap/index.html)
* Type “VIIRS chlorophyll” in the search box. \
  This will generate a list of choices
* Hover with your mouse on the question mark in the “Summary” column for some of the rows. \
  This is where you can find a brief description of each dataset&#x20;
* Click on the “graph” link to the left of the dataset named “Chlorophyll a Concentration, NPP VIIRS - CoastWatch - Weekly, 2012-present”&#x20;

Here is what you should see.&#x20;

![](<../.gitbook/assets/image (244).png>)

You'll notice that for this dataset, longitudes go from 0º to 360º instead of -180º to 180º. This allows users to download data for regions across the dateline. Other data sources, not focused on the Pacific, provide the data with longitudes between -180º and 180º.&#x20;

Notice also that for this dataset, latitudes go from North to South. \
Some datasets list the latitudes from south to north.

**You should always check the range of longitudes and latitudes for each dataset you are working with to make sure you are downloading data for the correct region and to avoid error messages.**

* Enter 18.5 and 20.5 as the south and north latitude and 203.5 and 206 as the start and stop longitude.&#x20;
* set the date to 06/02/2018
* Adjust the colorbar minimum to 0.005&#x20;
* Adjust the Scale parameter to "Log"
* Click on “redraw the graph”

![](<../.gitbook/assets/image (252).png>)

Scroll through the different time steps using the + button next to the date to see the full extent of the bloom (notice that there is a lot of cloud cover close to the island, that's the grey areas). You can also adjust the color scale by setting different values for colorbar minimum and maximum. \
Don't forget to click on "Redraw the Graph" after you change settings.

Under the "redraw the Graph" button, set the file type to ".largePng" and click on the "download" button. Try different file type options (html, PDF, ...).

## Sharing the map

After making all these changes, when the map looks the way you want it to, you can easily share it, or save it by simply copying the URL in your browser.

![](<../.gitbook/assets/image (292).png>)

## Griddap versus Tabledap

There are two types of data stored on ERDDAP – gridded data (i.e. satellite data) and tabular data (i.e. station or profile data). ERDDAP uses two different functions to deal with the different types of data. Griddap works with gridded data and Tabledap works with tabular data.&#x20;

Got to the [PACIOOS ERDDAP](https://pae-paha.pacioos.hawaii.edu/erddap/index.html) and click on "View a list of all 172 Datasets".

![](<../.gitbook/assets/image (79).png>)

You can see that there is a "GridDAP" column and a "TableDAP" column, corresponding to different datasets.

## Example #2. Look at PIFSC CTD data

Go to the [OceanWatch Central Pacific ERDDAP](https://oceanwatch.pifsc.noaa.gov/erddap/index.html) and click on the "graph" link to the left of the dataset named "PIFSC CTD Data".

This form allows you to plot a subset of the CTD data that was collected over a number of cruises, using a set of constraints.

Let's look at cruise "HA1101".

* In the first row of the "Constraints" column, select the variable "LEG\_NAME" using the drop down menu.
* Under "Optional constraint #1", another drop down menu appears, allowing you to select specific cruise legs. Select "HA1101\_LEG\_I".
* Add a second constraint, to look at depths ("DEPTH\_SW\_M") shallower than 20m.
* Set the color scale to reflect water temperature by selecting the "Temperature" variable in "Color", under "graph type".
* click on "redraw graph".

![](<../.gitbook/assets/image (20).png>)

Let's now make a traditional temperature/salinity plot:

* Below "graph type", select "salinity" as the "X Axis", and "temperature" as the "Y Axis", and "DEPTH\_SW\_M" as the "Color".
* Remove the depth constraint by selecting the blank space at the top of the drop down menu
* Under "Graph settings", select "circle" as the marker type, white as the "color", and set the color bar maximum to 600 (that is about the maximal depth in the dataset)
* click on "redraw graph"

![](<../.gitbook/assets/image (63).png>)

## Example #3. Look at wind data from Hurricane Katrina

Go to: [https://coastwatch.pfeg.noaa.gov/erddap/griddap/erdQSdivmod3day.graph](https://coastwatch.pfeg.noaa.gov/erddap/griddap/erdQSdivmod3day.graph)

* Select the "mod" variable - that's the absolute value of wind speed
* Change the region to 10-40N, 260-300E
* Change the date to 08/26/2005
* Change the color scale
* click on "redraw graph"

![](<../.gitbook/assets/image (76).png>)

* Go to: [https://coastwatch.pfeg.noaa.gov/erddap/griddap/erdQSwind3day.graph](https://coastwatch.pfeg.noaa.gov/erddap/griddap/erdQSwind3day.graph)
* Change the "Graph Type" to "vectors"
* Change "Vector X" to "x_wind" and "Vector Y" to "y\__wind"

![](<../.gitbook/assets/image (105).png>)

## Example #4. Examine the 1998 El Niño

Go to the [OceanWatch Central Pacific ERDDAP](https://oceanwatch.pifsc.noaa.gov/erddap/index.html) and click on the "graph" link to the left of the dataset named "Sea Surface Temperature, Coral Reef Watch, CoralTemp v3.1- Monthly, 1985-present".

* Make a map of SST for January 1997, for the region: -20 - 20N, 180 to 300E, and adjust the color scale to 18-30ºC
* Click on "Redraw the Graph"

![SST for January 1997](<../.gitbook/assets/image (122).png>)

* Make a map of SST for January 1998, for same region and adjust the color scale
* Click on "Redraw the Graph"

![](<../.gitbook/assets/image (159).png>)

We can clearly see the tongue of warm water due to the 1998 El Niño.

Now let's make a **Hovmöller plot**:&#x20;

* Below "Graph Type", select "time" in the drop down menu for "Y Axis".&#x20;
* Adjust the date range to jan. 1995 - Dec. 2000&#x20;
* Adjust the latitude to 0º, and the longitude to 180 to 300º
* Adjust the color scale to 18-30ºC
* Click on "Redraw the Graph"

![](<../.gitbook/assets/image (72).png>)

Again, the winter of 1998 was clearly anomalous compared to other years.

## Understanding the URL generated by ERDDAP

Do you have a graph you like? Want to save it or send it to someone? Change the drop-down menu next to “set the File Type” to png and click on “download the data”, that will create a png file with just that image in it.&#x20;

You can copy the url and send it to someone which will recreate the image. The url can also be edited.&#x20;

We’ll walk through some examples using the url created in Example #1:

[https://oceanwatch.pifsc.noaa.gov/erddap/griddap/noaa\_snpp\_chla\_weekly.graph?chlor\_a\[(2018-06-04T12:00:00Z)\]\[(0.0)\]\[(20.49375):(18.50625)\]\[(203.4938):(206.0063)\]&.draw=surface&.vars=longitude%7Clatitude%7Cchlor\_a&.colorBar=%7C%7CLog%7C0.005%7C%7C&.bgColor=0xffffffff\
](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/noaa\_snpp\_chla\_weekly.graph?chlor\_a\[\(2018-06-04T12:00:00Z\)]\[\(0.0\)]\[\(20.49375\):\(18.50625\)]\[\(203.4938\):\(206.0063\)]&.draw=surface&.vars=longitude%7Clatitude%7Cchlor\_a&.colorBar=%7C%7CLog%7C0.005%7C%7C&.bgColor=0xffffffff)

*   Base ERDDAP URL:

    `https://oceanwatch.pifsc.noaa.gov/erddap/griddap/`\

* Dataset ID:\
  `noaa_snpp_chla_weekly` \
  We could use `noaa_snpp_chla_monthly` instead.\

* File type:\
  `.graph`
  * Changing `graph` to `png` or `largePng` will create a png file of the image&#x20;
  * Changing `graph` to `csv` will download a CSV file to your computer. \
    A complete list of the available file format options can be viewed in the dropdown menu next to “Set the File Type”
  * Changing `graph` to `html` will bring up the form to download the data \

* Variable name:\
  `chlor_a` \
  Some datasets contain several variables. For example, wind data typically has a wind speed variable, a u-component variable and a v-component variable. \

* Time:\
  `[(2018-06-04T12:00:00Z)]`
  * Changing the date to `last` will ensure the graph always plots the most recent data \

* Latitude range:\
  `[(20.49375):(18.50625)]`\

* Longitude range:\
  `[(203.4938):(206.0063)]`\

* &#x20;Everything beginning with `&.draw` adjusts the look of the image\
  `&.draw=surface&.vars=longitude%7Clatitude%7Cchlor_a&.colorBar=%7C%7CLog%7C0.005%7C%7C&.bgColor=0xffffffff`

## Example #5. On your own. Chlorophyll time series

* First, create a map of a monthly composite of AQUA MODIS chlorophyll concentration around Hawaii for the date of your choice.&#x20;
* Create a time series of monthly chlorophyll concentration for a location close to Honolulu. \
  Hint: you will need to change the "Graph Type". Make sure to select of few years worth of data. Make sure your longitude is within the correct range and your latitudes in the correct order
* If there are gaps or outlier values, try again for a location further south (i.e. slightly further from the coast and shallow water)&#x20;
* Do you see any seasonal variation?&#x20;
* Download the time series data as a .csv file&#x20;
* Select a date for a period of low chlorophyll and create a map in a new browser window for that date&#x20;
* Open a new browser window, copy and paste the URL for the first map and create a map for a period of high chlorophyll by changing only the date in the URL&#x20;
* Compare the two maps and save them as .png

## Downloading the data

You can easily download any of the data on ERDDAP in a variety of different formats: .nc, .mat, .asc, etc.&#x20;

To the left of any dataset on the main ERDDAP page, click on “data” instead of "graph". \
ERDDAP generates a Data Access Form, where you can specify constraints to get the data you need: time range, latitude range, longitude range, altitude, data variables, and file type. You can then access the resulting data file via a URL, or use the Submit button to download the file to your computer.&#x20;

If you are making a graph of the data (on the page that says “Make A Graph”) just click on the “Data Access Form” link above the graph. You can also access this form by replacing the “.graph” in the url with “.html”.

## Using ERDDAP URLs in your software application

ERDDAP URL’s can be used to directly access data in any application, programming language or scripting language that can send a URL and receive a file (such as Python, Java, php, JavaScript, shell scripts using “curl” or “wget”), as well as from OPeNDAP enabled applications clients such as R, Matlab, GrADS, Ferret, and IDL.&#x20;

Many programming and scripting languages such as Java, python, php, and JavaScript can manipulate ERDDAP URL’s to import data for research or modeling, or for use in dynamic web pages.

## ERDDAP Interpolate Tool

If you do not work with any software but still want to match satellite data to some in-situ data, you can use the browser-based Interpolate Tool.

To access the tool, you need to append "/convert/interpolate.html" to the ERDDAP base URL:\
[https://oceanwatch.pifsc.noaa.gov/erddap/convert/interpolate.html](https://oceanwatch.pifsc.noaa.gov/erddap/convert/interpolate.html)\
[https://coastwatch.pfeg.noaa.gov/erddap/convert/interpolate.html](https://coastwatch.pfeg.noaa.gov/erddap/convert/interpolate.html)

To use the tool, you need to format your in-situ data locations and dates correctly, to match what you see in the pre-set example:

![](<../.gitbook/assets/image (306).png>)

This can be done in Excel. Select all your dates, click right and select "Format Cells". In the left-side column, click on "Date", then on "Custom":

![](<../.gitbook/assets/image (258).png>)

You can then edit the Date format by typing: yyyy-mm-dd

Most satellite data you will work with is at best daily, so you can ignore the time component.\
If you need the time component, if you have a separate column for date and time, create an additional column, and make it the sum of your date and time column. Then format the new column using the format: yyyy-mm-ddThh:mmZ

Now, identify, which ERDDAP dataset you want to work with, for example: Daily SST: [https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW\_sst\_v1\_0.graph](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW\_sst\_v1\_0.graph)

![](<../.gitbook/assets/image (301) (1).png>)

Note the dataset ID in red, the name of the variable in green, and make sure that your longitudes match the longitude format (0-360º vs -180 to 180º). Transform your longitudes if needed. Save your file as a CSV file. Then open it in notepad, and copy paste the data into the browser. Edit the dataset ID and variable name in the "request CSV" line, as well as any other option. Edit The "File type" for the output and click on "Convert".

![](<../.gitbook/assets/image (220).png>)

The resulting file will have a value of SST for each data point!

Now you try it with this example file!\
[https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/track.csv](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/track.csv)



