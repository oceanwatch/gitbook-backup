# index

## Python Tutorial - How to work with OceanWatch data in Python

This tutorial will show the steps to grab data in ERDDAP from Python, how to work with NetCDF files in Python and how to make some maps and time-series od chlorophyll-a concentration around the main Hawaiian islands

### 1. Downlading data from Python

Because ERDDAP includes RESTful services, you can download data listed on any ERDDAP platform from R using the URL structure. For example, the following page allows you to subset monthly Chlorophyll a data from the Aqua-MODIS sensor [https://oceanwatch.pifsc.noaa.gov/erddap/griddap/OceanWatch\_aqua\_chla\_monthly.html](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/OceanWatch_aqua_chla_monthly.html). Select your region and date range of interest, then select the '.nc' \(NetCDF\) file type and click on "Just Generate the URL".

In this specific example, the URL we generated is : [https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW\_sst\_v1\_0\_monthly.nc?analysed\_sst\[\(2018-01-01T12:00:00Z\):1:\(2018-12-01T12:00:00Z\)\]\[\(17\):1:\(30\)\]\[\(195\):1:\(210](https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW_sst_v1_0_monthly.nc?analysed_sst[%282018-01-01T12:00:00Z%29:1:%282018-12-01T12:00:00Z%29][%2817%29:1:%2830%29][%28195%29:1:%28210)\)\]

In Python, run the following to download the data using the generated URL :

```python
import urllib.request
url="https://oceanwatch.pifsc.noaa.gov/erddap/griddap/CRW_sst_v1_0_monthly.nc?analysed_sst[(2018-01-01T12:00:00Z):1:(2018-12-01T12:00:00Z)][(17):1:(30)][(195):1:(210)]"
urllib.request.urlretrieve(url, "sst.nc")
```

```text
('sst.nc', <http.client.HTTPMessage at 0x2a195863be0>)
```

## 2. Importing NetCDF4 data in Python

Now that we've downloaded the data locally, we can import it and extract our variables of interest.

The xarray package makes it very convenient to work with NetCDF files. Documentation is available here: [http://xarray.pydata.org/en/stable/why-xarray.html](http://xarray.pydata.org/en/stable/why-xarray.html)

```python
import xarray as xr
import netCDF4 as nc
```

* Open the file and load it as an xarray dataset:

```python
ds = xr.open_dataset('sst.nc',decode_cf=False)
```

* examine the data structure:

```python
ds
```

```text
<xarray.Dataset>
Dimensions:       (latitude: 261, longitude: 301, time: 12)
Coordinates:
  * time          (time) float64 1.515e+09 1.517e+09 ... 1.541e+09 1.544e+09
  * latitude      (latitude) float32 17.025 17.075 17.125 ... 29.975 30.025
  * longitude     (longitude) float32 195.025 195.075 ... 209.975 210.025
Data variables:
    analysed_sst  (time, latitude, longitude) float64 ...
Attributes:
    acknowledgement:            NOAA Coral Reef Watch Program
    cdm_data_type:              Grid
    comment:                    This product is designed to improve on and re...
    contributor_name:           NOAA Coral Reef Watch program
    contributor_role:           Collecting source data and deriving products;...
    Conventions:                CF-1.6, ACDD-1.3, COARDS
    creator_email:              coralreefwatch@noaa.gov
    creator_institution:        NOAA/NESDIS/STAR Coral Reef Watch program
    creator_name:               NOAA Coral Reef Watch program
    creator_type:               group
    creator_url:                https://coralreefwatch.noaa.gov/
    data_source:                NOAA Daily Global 5km Geo-Polar Blended Night...
    date_created:               2018-01-01T00:00:00Z
    date_issued:                2018-12-02T15:20:07Z
    date_metadata_modified:     2018-09-01T00:00:00Z
    date_modified:              2018-01-01T00:00:00Z
    Easternmost_Easting:        210.025
    geospatial_bounds:          "POLYGON((-90.0 360.0, 90.0 360.0, 90.0 0.0, ...
    geospatial_bounds_crs:      EPSG:32663
    geospatial_lat_max:         30.025
    geospatial_lat_min:         17.025
    geospatial_lat_resolution:  0.049999999999999996
    geospatial_lat_units:       degrees_north
    geospatial_lon_max:         210.025
    geospatial_lon_min:         195.025
    geospatial_lon_resolution:  0.05000000000000001
    geospatial_lon_units:       degrees_east
    history:                    Mon Mar  2 06:00:23 2020: ncatted -O -a geosp...
    id:                         CoralTemp-v1.0
    infoUrl:                    https://coralreefwatch.noaa.gov/satellite/ble...
    institution:                NOAA/NESDIS/STAR Coral Reef Watch program
    instrument:                 ATSR-1, ATSR-2, AATSR, AVHRR, AVHRR-2, AVHRR-...
    instrument_vocabulary:      NOAA NODC Ocean Archive System Instruments
    keywords:                   5km, analysed, analysed_sst, analysis, blende...
    keywords_vocabulary:        GCMD Science Keywords
    license:                    OSTIA Usage Statement (1985-2002): IMPORTANT ...
    metadata_link:              https://coralreefwatch.noaa.gov/satellite/ble...
    naming_authority:           gov.noaa.coralreefwatch
    NCO:                        4.3.7
    nco_openmp_thread_number:   1
    Northernmost_Northing:      30.025
    platform:                   Ships, drifting buoys, moored buoys, TOGA-TAO...
    platform_vocabulary:        NOAA NODC Ocean Archive System Platforms
    processing_level:           L4
    product_version:            1.0
    program:                    NOAA Coral Reef Watch program
    project:                    NOAA Coral Reef Watch program
    publisher_email:            coralreefwatch@noaa.gov
    publisher_institution:      NOAA/NESDIS/STAR Coral Reef Watch program
    publisher_name:             NOAA Coral Reef Watch program
    publisher_type:             group
    publisher_url:              https://coralreefwatch.noaa.gov/
    references:                 Donlon, et al., 2011. The Operational Sea Sur...
    source:                     OSTIA Sea Surface Temperature Reanalysis (nig...
    sourceUrl:                  (local files)
    Southernmost_Northing:      17.025
    standard_name_vocabulary:   CF Standard Name Table v27
    summary:                    CoralTemp 5km gap-free analysed blended sea s...
    time_coverage_duration:     P1D
    time_coverage_end:          2018-12-01T12:00:00Z
    time_coverage_resolution:   P1D
    time_coverage_start:        2018-01-01T12:00:00Z
    title:                      Sea Surface Temperature, Coral Reef Watch, Co...
    Westernmost_Easting:        195.025
```

* examine which coordinates and variables are included in the dataset:

```python
ds.coords
```

```text
Coordinates:
  * time       (time) float64 1.515e+09 1.517e+09 ... 1.541e+09 1.544e+09
  * latitude   (latitude) float32 17.025 17.075 17.125 ... 29.925 29.975 30.025
  * longitude  (longitude) float32 195.025 195.075 195.125 ... 209.975 210.025
```

```python
ds.data_vars
```

```text
Data variables:
    analysed_sst  (time, latitude, longitude) float64 ...
```

* examine the structure of analysed\_sst:

```python
ds.analysed_sst.shape
```

```text
(12, 261, 301)
```

Our dataset is a 3-D array with 261 rows corresponding to latitudes and 301 columns corresponding to longitudes, for each of the 12 time steps.

* get the dates for each time step:

```python
ds.time
```

```text
<xarray.DataArray 'time' (time: 12)>
array([1.514808e+09, 1.517486e+09, 1.519906e+09, 1.522584e+09, 1.525176e+09,
       1.527854e+09, 1.530446e+09, 1.533125e+09, 1.535803e+09, 1.538395e+09,
       1.541074e+09, 1.543666e+09])
Coordinates:
  * time     (time) float64 1.515e+09 1.517e+09 1.52e+09 ... 1.541e+09 1.544e+09
Attributes:
    _CoordinateAxisType:    Time
    actual_range:           [1.5148080e+09 1.5436656e+09]
    axis:                   T
    coverage_content_type:  coordinate
    ioos_category:          Time
    long_name:              reference time of the sst field
    standard_name:          time
    time_origin:            01-JAN-1970 00:00:00
    units:                  seconds since 1970-01-01T00:00:00Z
```

```python
dates=nc.num2date(ds.time,ds.time.units)
dates
```

```text
array([datetime.datetime(2018, 1, 1, 12, 0),
       datetime.datetime(2018, 2, 1, 12, 0),
       datetime.datetime(2018, 3, 1, 12, 0),
       datetime.datetime(2018, 4, 1, 12, 0),
       datetime.datetime(2018, 5, 1, 12, 0),
       datetime.datetime(2018, 6, 1, 12, 0),
       datetime.datetime(2018, 7, 1, 12, 0),
       datetime.datetime(2018, 8, 1, 12, 0),
       datetime.datetime(2018, 9, 1, 12, 0),
       datetime.datetime(2018, 10, 1, 12, 0),
       datetime.datetime(2018, 11, 1, 12, 0),
       datetime.datetime(2018, 12, 1, 12, 0)], dtype=object)
```

### Working with the extracted data

#### Creating a map for one time step

Let's create a map of SST for January 2018 \(our first time step\).

```python
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
from matplotlib.colors import LinearSegmentedColormap
np.warnings.filterwarnings('ignore')
```

* set some color breaks

```python
np.nanmin(ds.analysed_sst)
```

```text
17.922142857142862
```

```python
np.nanmax(ds.analysed_sst)
```

```text
28.390645161290323
```

```python
levs = np.arange(17.5, 28.5, 0.05)
```

* define a color palette

```python
jet=["blue", "#007FFF", "cyan","#7FFF7F", "yellow", "#FF7F00", "red", "#7F0000"]
```

* set color scale using the jet palette

```python
cm = LinearSegmentedColormap.from_list('my_jet', jet, N=len(levs))
```

* plot the SST map

```python
plt.contourf(ds.longitude, ds.latitude, ds.analysed_sst[0,:,:], levs,cmap=cm)
#plot the color scale
plt.colorbar()
#example of how to add points to the map
plt.scatter(range(202,206),np.repeat(26,4),c='black')
#example of how to add a contour line
plt.contour(ds.longitude, ds.latitude, ds.analysed_sst[0,:,:],levels=20,linewidths=1)
#plot title
plt.title("Monthly Sea Surface Temperature " + dates[0].strftime('%b %Y'))
plt.show()
```

#### Plotting a time series

Let's pick the following box : 18-23N, 200-206E. We are going to generate a time series of mean SST within that box.

* first, let subset our data:

```python
lat_bnds, lon_bnds = [18, 23], [200, 206]
da=ds.sel(latitude=slice(*lat_bnds), longitude=slice(*lon_bnds))
```

* let's plot the subset:

```python
plt.contourf(da.longitude, da.latitude, da.analysed_sst[0,:,:], levs,cmap=cm)
plt.colorbar()
plt.title("Monthly Sea Surface Temperature " + dates[0].strftime('%b %Y'))
plt.show()
```

* let's compute the monthly mean over the bounding region:

```python
res=np.mean(da.analysed_sst,axis=(1,2))
```

* let's plot the time-series:

```python
plt.figure(figsize=(8,4))
plt.scatter(dates,res)
plt.ylabel('SST (ºC)')
```

```text
Text(0,0.5,'SST (ºC)')
```

#### Creating a map of average SST over a year

* let's compute the yearly mean for the region:

```python
mean_sst=np.mean(ds.analysed_sst,axis=0)
```

```python
mean_sst.shape
```

```text
(261, 301)
```

* let's plot the map of the 2018 average SST in the region:

```python
plt.contourf(ds.longitude, ds.latitude, mean_sst, levs,cmap=cm)
plt.colorbar()
plt.title("Mean SST " + dates[0].strftime('%Y-%m')+' - '+dates[11].strftime('%Y-%m'))
plt.show()
```

