# NetCDF and Panoply tutorial

![From Xkcd.com](<../.gitbook/assets/image (86).png>)



## NetCDF

N**etCDF (Network Common Data Form)** is a file format for storing multidimensional scientific data (variables) such as temperature, salinity, chlorophyll concentration, wind speed, ...

Many organizations and scientific groups in different countries have adopted netCDF as a standard way to represent some forms of scientific data.

The NetCDF format has many advantages, the most important of which is that it is **self-describing**, meaning that software packages can directly read the data and determine its structure, the variable names and essential metadata such as the units. This self-describing aspect of the netCDF file format means that the information needed to ensure accurate work (reduce the incidence of errors) is available within the data itself (no need for additional files). Secondly, it means that different analysis software, like Matlab, R, Python or ArcGIS (among many others), have utilities to read and work with NetCDF files. Thirdly, plotting software (e.g. Ferret, **Panoply**, ncview) can directly read the netCDF files for visualization.

![Example of embedded metadata within a NetDCF file](<../.gitbook/assets/image (59).png>)

![Example structure of a NetCDF file containing temperature and precipitation data across a region for 8 time steps](<../.gitbook/assets/image (8).png>)

## NASA Panoply

NASA developed a viewer that allows users to create images of NetCDF files.\
Panoply is available for download at: [https://www.giss.nasa.gov/tools/panoply/](https://www.giss.nasa.gov/tools/panoply/) and can be run on Windows, Mac and Linux computers. In Windows, you do not need to install it, just download it and double-click on the Panoply.exe file. It can take a while to launch, be patient.

## 1. Make a map of global chlorophyll a concentration

* Download a file of cumulative mean of chlorophyll a concentration here:\
  [https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/A20021852018090.L3m\_CU\_CHL\_chlor\_a\_4km.nc](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/A20021852018090.L3m\_CU\_CHL\_chlor\_a\_4km.nc)
* Launch Panoply.&#x20;
* When Panoply opens, it prompts you to open a file. Open the file you just downloaded.

![Panoply interface](<../.gitbook/assets/image (37) (1).png>)

On the left side, Panoply lists the variables contained in the file (longitude, latitude, chlorophyll concentration).&#x20;

On the right side, it displays the file’s metadata. You can scroll down to get more details. \
****For example, in the global attributes, you will find the platform (this is data from the Aqua satellite), the instrument (MODIS), the processing version (2018.0), the time coverage (2002 to 2018). There is no time variable however, this is a cumulative mean over the time period. Notice you didn’t need to download any ancillary files to access all the metadata, it’s embedded in the one file you downloaded.

* Find the identifier\_product\_doi in the list of global attributes. Copy it in the doi field on this [website](http://dx.doi.org). This should lead you here: [https://oceancolor.gsfc.nasa.gov/data/10.5067/AQUA/MODIS/L3M/CHL/2018/](https://oceancolor.gsfc.nasa.gov/data/10.5067/AQUA/MODIS/L3M/CHL/2018/) \
  This page contains extra information about the data if you are interested in reading more about it. \
  Metadata varies from file to file depending on how much information is provided by the person/institution who generated the file.&#x20;
* Next, on the left side of the screen, double click on the chlor\_a variable. Keep the default settings and click Create. \
  (this will take a minute, it’s a big file)

![](<../.gitbook/assets/image (175).png>)

Panoply generated an image of the chlorophyll data contained in the file.&#x20;

* Above the image, click on the “Array 1” submenu. \
  This shows you all the values of chlorophyll concentration contained in the file for each longitude/latitude pixel.&#x20;

We now need to adjust the color scale and tweak some of the image options. \
Note: There may be a lag between clicking or adjusting values, and results. It’s a big file.&#x20;

* Below the image, click on the “scale” submenu.&#x20;
  * Change the “Units” from “scalar” to “log10”.&#x20;
  * Adjust the color scale to 0.02 to 2.0.
  * In “Color Table” you have many options of color palettes. I like the “MPL\_viridis.rgb” for chlorophyll concentration, but you can choose whichever one you prefer. \

* Next click on the “Map” submenu (if you are on a Mac, it's the "Grid" submenu), and&#x20;
  * change the map projection to “Mollweide Oblique”.
  * change “Center on: Lon.” to 180º.
  * change “Grid: style” to none if you want to remove the longitude/latitude grid. \

* Click on the “Labels” submenu&#x20;
  * uncheck the “Center footnote” box.&#x20;
  * edit the Title to “AQUA MODIS Chlorophyll Concentration, 2002 – 2018” \

* Finally, save the image to your computer (File > Save image).&#x20;

![](<../.gitbook/assets/image (88).png>)

You can also go to: [https://www.giss.nasa.gov/tools/panoply/colorbars/](https://www.giss.nasa.gov/tools/panoply/colorbars/) to download additional color palettes. Download another palette for chlorophyll, open it in Panoply, then change the color palette for your image to this new one. Save the image to your computer.

## 2. Make a map of global SST

Download a file of global Sea Surface Temperature :&#x20;

[https://drive.google.com/file/d/1btWAG8Vi9SABGi6NesDRpAOnFQlaN8VD/view?usp=sharing](https://drive.google.com/file/d/1btWAG8Vi9SABGi6NesDRpAOnFQlaN8VD/view?usp=sharing)

Open it in Panoply. Scroll down the list of metadata. You can see it looks different from the metadata for the previous file.&#x20;

This is a blended product. Identify the name of the instruments and satellites the data come from. How many satellites were used to create this gap-free SST dataset?&#x20;

Following the same steps as above, create an image of the “analysed\_sst” variable with an appropriate color scale. (You do not need to use a log scale for SST though).

* Change the units to ºC or ºF.&#x20;
* Click on “Fit to Data” to adjust the color scale or adjust the range of values manually.&#x20;
* Adjust the title with the file’s date.&#x20;
* Save to your computer.

![](<../.gitbook/assets/image (100).png>)

## 3. Zooming in on a region

Close any graphics window.&#x20;

* Double-click on “analysed\_sst” again and click ok.&#x20;
* To zoom in on a region, type “Ctrl” ("Command" on Mac). You will see that your cursor changes to a magnifying glass. While keeping the “Ctrl” key down, click and drag over a region of interest. This will generate a plot of SST for that region only. Under the "Map" tab, click on the "Fix proportions" button.

![](<../.gitbook/assets/image (197).png>)

## 4. Files with multiple time steps

Download chl-a data for several months using the following URL:

{% embed url="https://oceanwatch.pifsc.noaa.gov/erddap/griddap/noaa_snpp_chla_monthly.nc?chlor_a[(2019-02-01T12:00:00Z):1:(2019-11-01T12:00:00Z)][(39.99375):1:(15.01875)][(179.9813):1:(210.0188)]" %}

* Open it in Panoply \
  This is monthly chlorophyll concentration data from the VIIRS instrument, on the Suomi-NPP satellite for the Hawaii region.
* Zoom in on the Hawaii region where there is data.&#x20;
* Adjust the scale to a log scale and an appropriate range of values&#x20;
* Click on the “Array(s)” tab. There you can select a specific time step. Scroll through the dates and save a plot.

![](<../.gitbook/assets/image (119) (1).png>)

## 5. Vector plots

(adapted from here: [http://davidburchnavigation.blogspot.com/2020/01/viewing-netcdf-weather-files-in-panoply.html](http://davidburchnavigation.blogspot.com/2020/01/viewing-netcdf-weather-files-in-panoply.html))

Let's look at wind data: [https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/CCMP\_RT\_Wind\_Analysis\_20210122\_V02.1\_L3.0\_RSS.nc](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/CCMP\_RT\_Wind\_Analysis\_20210122\_V02.1\_L3.0\_RSS.nc)

1. Open the file in Panoply, you can see there 2 main variables, uwnd (the east-west component of the wind speed vectors) and vwnd (the north-south component).
2. Double-click on uwnd and click "create". You get a color map of the East-West component of the wind speed for that day, which by itself, is not very insightful. We are used to wind maps looking different, with a color map for wind speed values and arrows for wind direction. Luckily, Panoply allows us to create vector maps.
3. Double-click on vwnd, click on "create", then in the main Panoply window, click on "combine plot".

![](<../.gitbook/assets/image (242).png>)

4\. In the "combine plot" menu that pops up, select uwnd and click on "combine". Notice that you now have two data arrays in the same window.\
5\. In the "Arrays" tab, click on the drop down menu that says "Array 1 - Array 2" and select "Vector Magnitude". You now have a vector plot!

![](<../.gitbook/assets/image (281).png>)

6\. You can now edit the color scale (select "fit to data" then adjust if needed), change the unit to knots if you wish, change the projection, edit the title as we've seen earlier.\
7\. Finally, you can change the value of wind speed that each arrow represents to a nice round value like 20 for example.

![Voilà!](<../.gitbook/assets/image (177).png>)

## References:

&#x20;[https://www.unidata.ucar.edu/software/netcdf/docs/netcdf\_introduction.html](https://www.unidata.ucar.edu/software/netcdf/docs/netcdf\_introduction.html)&#x20;

[https://www.unidata.ucar.edu/software/netcdf/docs/faq.html#whatisit](https://www.unidata.ucar.edu/software/netcdf/docs/faq.html#whatisit)

[https://www.giss.nasa.gov/tools/panoply/](https://www.giss.nasa.gov/tools/panoply/)&#x20;

[http://pro.arcgis.com/en/pro-app/help/data/multidimensional/a-quick-tour-of-netcdf-data.htm](http://pro.arcgis.com/en/pro-app/help/data/multidimensional/a-quick-tour-of-netcdf-data.htm)&#x20;

[https://www.nodc.noaa.gov/woce/woce\_v3/wocedata\_1/cmdac/primer/why.htm](https://www.nodc.noaa.gov/woce/woce\_v3/wocedata\_1/cmdac/primer/why.htm)&#x20;

[https://www.researchgate.net/publication/315950787\_xarray\_N-D\_labeled\_Arrays\_and\_Datasets\_in\_Python](https://www.researchgate.net/publication/315950787\_xarray\_N-D\_labeled\_Arrays\_and\_Datasets\_in\_Python)&#x20;

[http://davidburchnavigation.blogspot.com/2020/01/viewing-netcdf-weather-files-in-panoply.html](http://davidburchnavigation.blogspot.com/2020/01/viewing-netcdf-weather-files-in-panoply.html)

[https://xkcd.com/](https://xkcd.com)









