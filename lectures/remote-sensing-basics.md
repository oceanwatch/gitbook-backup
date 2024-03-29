# Remote Sensing Basics

This Lecture is also available as an audio-narrated PowerPoint presention:  
 - [Part 1](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/01-Satellite101_Part1.pptx)  
 - [Part 2](https://oceanwatch.pifsc.noaa.gov/files/hawaii2020/02-Satellite101_Part2.pptx)

## Objectives

Establish baseline vocabulary/concepts: 

* Satellite vs sensor Active vs passive sensor 
* Electromagnetic radiation 
* Geophysical variable/product 
* Atmospheric windows 
* Atmospheric correction 
* Polar vs geostationary orbit 
* Spatial, temporal resolution, swath width 
* Wavelength band/channel 
* Data levels 
* Temporal composites vs cloud cover 
* Near-Real Time vs. Science Quality

## Advantages of satellite remote sensing

* Provides information where surface-based measurements are not available and augments existing measurements
* Provides global/near-global coverage with consistent observations

## Satellite vs Sensor

* Satellite: a space-borne platform holding one or more sensors \(instruments\) making measurements
* Some satellites are single-mission, carrying only one sensor:  e.g. the SeaWiFS sensor on the GeoEye/OrbImage satellite
* Other satellites have multiple sensors on them:  e.g. MODIS is one of 6 sensors on the Aqua satellite.  There is also a MODIS sensor on the Terra satellite.

![](../.gitbook/assets/image%20%2839%29.png)

![The NOAA GOES-R satellite and its instruments](../.gitbook/assets/image%20%287%29.png)

## What is measured by the sensors?

Sensors can NOT directly measure populations of most fish, whales, turtles, monk seals, etc.

![](../.gitbook/assets/image%20%28123%29.png)

Satellite data can provide information about oceanic parameters that influence marine resources:   
SST, Currents, Wind, Ocean color, Salinity

![](../.gitbook/assets/image%20%2816%29.png)

Satellite sensors measure electromagnetic radiation \(EMR\) that is emitted or reflected by the ocean \(and land\).   
Sensors target specific sets of wavelengths depending on their application  
After \(many\) corrections and calibrations, algorithms are used to calculate geophysical products \(SST, chla concentration, wind speed, …\)

![From Robinson, Discovering the Ocean from Space](../.gitbook/assets/image%20%28112%29.png)

![](../.gitbook/assets/image%20%28145%29.png)

Visible and IR \(Infrared\) radiation is typically measured in wavelengths.   
Microwaves are measured in frequency.  
Microwave frequencies are often described by letters, the C-band, the X-band etc.

![Different satellite applications operating in different part of the electromagnetic spectrum](../.gitbook/assets/image%20%28121%29.png)

## Sensor types \(active vs passive\)

Passive sensors measure electromagnetic radiation that has a natural origin:   
- Solar radiation reflected or scattered from the Earth’s surface   
- Thermal radiation emitted from the Earth’s surface

Active sensors measure electromagnetic radiation generated by the satellite that is:   
- sent down to the Earth’s surface   
- and reflected or scattered back to the satellite

![](../.gitbook/assets/image%20%28109%29.png)

* Passive Remote Sensing: Reception of emitted, reflected or scattered EMR at the satellite sensor, after it travels from the ocean through the atmosphere: used with UV, visible, IR and microwave wavelengths/frequencies.
* Active Remote Sensing: Reception of the reflection of a transmitted pulse of EMR, after interacting with the surface of the ocean and travelling through the atmosphere \(twice\). Examples include: altimeters, scatterometers, lidars, radars.

## Electromagnetic radiation \(EMR\)

Most solar energy comes to the earth as short wavelength electromagnetic radiation \(UV, visible light\) and is re-radiated \(emitted\) back to space as long wavelength electromagnetic radiation \(infrared, microwaves\)

![](../.gitbook/assets/image%20%2813%29.png)



## The influence of the atmosphere

* All radiation is influenced by the atmosphere in various ways: The sun's radiation is scattered, reflected or absorbed by particles in the atmosphere as is the radiation reflected by the Earth’s surface.
* Satellites look at the earth surface through the atmosphere.

![Credit: Jan Yoshioka, CI](../.gitbook/assets/image%20%2817%29%20%281%29%20%281%29.png)



* The influence of the atmosphere depends on the wavelength of EMR. The atmosphere is opaque to electromagnetic radiation at many wavelengths, due to absorption by atmospheric gases. There are only certain wavelengths through which radiation may be fully or partly transmitted.
* Remote sensing focuses on those transmissive ranges, the so-called atmospheric windows.

![source: NASA](../.gitbook/assets/image%20%28136%29.png)

![Where satellites can &quot;see&quot;: atmospheric windows](../.gitbook/assets/image%20%2846%29.png)

In the **visible**, where the sun emits at the highest intensity, the atmospheric transmittance is high.

![atmospheric window in the visible](../.gitbook/assets/image%20%28153%29.png)

At higher wavelengths, transmittance is reduced to narrow bands. This includes the optical windows in the **thermal infrared**, where the Earth's surface emits radiation.

![optical windows in the thermal infrared](../.gitbook/assets/image%20%28173%29.png)

In the **microwaves**, the atmosphere is nearly transmissive, but the sun and earth's radiation are weak \(need large antennas to collect enough radiation\)

![microwave range](../.gitbook/assets/image%20%2834%29.png)

Wavelengths shorter than the **ultraviolet** are nearly totally absorbed by the atmosphere and are therefore less relevant for remote sensing.

![UV range](../.gitbook/assets/image%20%28142%29.png)

## Atmospheric pathways

![](../.gitbook/assets/image%20%289%29.png)

**Ray 1 - the useful signal**  
Ray 2 - the radiation leaving the sea that is absorbed by the atmosphere  
Ray 3 - the radiation that is scattered by the atmosphere out of the sensor field of view  
Ray 4 - the energy emitted by the constituents of the atmosphere  
Ray 5 - the energy reflected by scattering into the field of vision of the sensor  
Ray 6 - the energy that left the sea surface but from outside the field of view.

Even at “window” wavelengths, atmospheric correction of the satellite data is necessary to derive accurate satellite data products.

![](../.gitbook/assets/image%20%2862%29.png)

The ocean area within the sensor’s field of view emits rays 1+2+3

Rays 4, 5, and 6 reach the sensor from outside of the sea surface in the field of view, and therefore constitute extraneous "noise" on top of the signal.

The sensor receives rays 1+4+5+6

**The complete atmospheric correction should result in the sum of rays 1+2+3.**

## How is EMR measured by sensors?

Satellite sensors measure the intensity of EMR at specific wavelengths using a telescope to focus the EMR onto a series of light detectors \(radiometers\). 

The configuration of the light detectors and telescope varies between sensor types, but in the end, all sensors produce a set of equally spaced boxes/pixels \(i.e., a 2-D array of measured values\) where each individual box/pixel contains the value of the intensity of EMR \(Watts m-2\) for a specific wavelength from each location on earth covered by the satellite.

![From Robinson, Discovering the Ocean from Space](../.gitbook/assets/image%20%28134%29.png)

The resulting 2-D array can be displayed as an image or it can be analyzed as a 2-D array of numbers

The size of the rectangular region on earth over which the instrument averages the EMR onto a single light detector is referred to as the instrument resolution. For example, 1-km resolution sensor averages EMR intensity over a 1-km by 1-km region on the earth \(at nadir, i.e. when the satellite is directly at the vertical\).

![EMR intensity at a specific wavelength, over a region](../.gitbook/assets/image%20%28104%29.png)

Multispectral radiometers measure EMR intensity at a few discrete wavelength regions. Each wavelength region is defined by a central wavelength and a small range of wavelengths around it \(a bandwidth\)

The intensity of EMR at each wavelength region is stored separately in a stack of digital images. Each separate image is called a wavelength band or a wavelength channel.

Each band or channel can be referred to by its central wavelength value or by sequential numbering \(1, 2, 3, …\) of each band from shortest to longest wavelength

![](../.gitbook/assets/image%20%28117%29%20%281%29%20%281%29%20%281%29.png)

## Higher order products

Several bands can be combined to produce higher order products.

Below is an example of making a true color image from the addition of separate R, G and B bands.



![Intensity of the 8 Visible and Near-Infrared Bands from the SeaWiFS Sensor for the East Coast of the US](../.gitbook/assets/image%20%28128%29%20%281%29%20%281%29.png)

![True-Color Image Created from bands 2, 5, and 6 ](../.gitbook/assets/image%20%2838%29%20%281%29.png)

Final Color Image = C1\*band2 + C2\*band5 + C3\*band6

## Types of Applications of Satellite Data

![From Robinson, Discovering the Ocean from Space](../.gitbook/assets/image%20%2835%29.png)

## Resolution

**Spatial resolution** is defined as the pixel size of an image representing the size of the surface area being measured on the ground and is determined by the sensors' instantaneous field of view \(IFOV\).

**Temporal resolution** is defined by the amount of time that passes between imagery collection periods.

**Swath width** of the satellite refers to the width of the area observed by the satellite. Satellites with larger swath widths will take less time to acquire global spatial coverage.

## Satellite orbits

The two major types of satellite orbits are:

* **Polar orbiting**: a single polar orbiting satellite can view the entire earth once a day
* **Geostationary**: a single geostationary satellite can view a limited region of the earth, but can do so continuously throughout the day

### Polar Orbiting

{% file src="../.gitbook/assets/polar-orbit-principle.mp4" caption="animation of a polar-orbiting satellite" %}

Credit: EUMETSAT

* Altitude: 700 -800km 
* ~ 14 orbits a day 
* Depending on the width of the swath, will cover almost the whole Earth in a day 
* Global coverage 
* High spatial resolution \(&lt; 1 km\) 
* Low temporal resolution \(≥ 1 day\)

![24h of chlorophyll-a data from the VIIRS instrument onboard the polar-orbiting NOAA-20 satellite](../.gitbook/assets/image%20%2847%29.png)

### Geostationary orbit

{% file src="../.gitbook/assets/geostationary-orbit.mp4" caption="animation of a satellite in geostationary orbit" %}

Credit: Omega Open Course

{% file src="../.gitbook/assets/goes-16-full-disk-geocolor-august-2017.mp4" caption="" %}

Credit: [http://rammb-slider.cira.colostate.edu](http://rammb-slider.cira.colostate.edu)

![Example: weather satellites. coverage of GOES-West \(US\), GOES-East \(US\), MeteoSat x2 \(Europe\), Himawari \(Japan\). &amp;gt;5 geostationary satellites are necessary to achieve global coverage](../.gitbook/assets/image%20%28139%29.png)

## A note on satellite names …

NOAA assigns a letter to the satellite before it is launched and a number once it has achieved orbit.

For the geostationary constellation, before being launched, GOES satellites are designated by letters \(A, B, C, etc.\). Once a GOES satellite is launched successfully, it is redesignated with a number \(1, 2, 3, etc.\). GOES-R, the first in NOAA's GOES-R series of satellites, was designated GOES-16 when it reached geostationary orbit. GOES-S became GOES-17.

Same for the polar-orbiting constellation: ITOS-A became NOAA-1. JPSS-1 was designated NOAA-20 when it reached its orbit.

GOES-A to GOES-F became GOES-1 to GOES-6.

Because GOES-G was a launch failure, it never received a number. GOES-H to GOES-R became GOES-7 to GOES-16 \(skipping GOES-Q, which was not built\).

The switch from pre-launch to on-orbit names allows to keep the name series intact for the on-orbit constellations.

## Levels of Data

* Level 0: Raw data received from satellite, in standard binary form
* Level 1: Unprocessed data in sensor’s geographic coordinates, containing calibration information
* Level 2: Derived geophysical variables atmospherically corrected and geolocated, but presented in sensor’s geographic coordinates \(granules\). Also sometimes referred to as “along-track” data.•

Most useful for fisheries research:

* Level 3: Derived geophysical variables mapped on uniform space-time grid scales. Spatial and temporal composites.
* Level 4: Model output or results from analyses of lower-level data \(e.g., variables derived from multiple measurements, like primary productivity\), or interpolation to provide cloud-free product

![From Robinson, Discovering the Ocean from Space](../.gitbook/assets/image%20%282%29.png)

### Levels of Data: L0 -&gt; L3 examples

![From Chassot et al. 2011](../.gitbook/assets/image%20%28129%29.png)

### Level-2 vs. Level-3 data

The sensor views the earth in a swath of individual scan lines as the satellite is moving

![](../.gitbook/assets/image%20%2851%29.png)

![View is &#x201C;distorted&#x201D;, pixels geolocated along scan line](../.gitbook/assets/image%20%2848%29.png)

![Pixels resampled to regular grid \(lat/lon\)](../.gitbook/assets/image%20%2852%29.png)

### Additional types of Level 3

* Level 3C: Level 3 Collated : Data from different time periods from the same sensor are collated together to create a more complete image. For example, GOES-16 collects data every 15 mins, a daily L3C product would collate all data from one day. This helps with cloud cover.
* Level 3S: Level 3 Super-collated: Data from various sensors are collated together. For example, data from geostationary and polar-orbiting sensors to take advantage of the strengths of both \(higher resolution vs less impact from clouds\).

### Level-3 data – Temporal composites

![GOES West Imager &#x2013; SST &#x2013; 1 hour, 09/15/2018](../.gitbook/assets/image%20%2850%29.png)

![GOES West Imager &#x2013; SST &#x2013; 1 day, 09/15/2018](../.gitbook/assets/image%20%28162%29.png)

![GOES West Imager &#x2013; SST &#x2013; 1 week, 09/12/2018 &#x2013; 09/18/2018](../.gitbook/assets/image%20%2830%29.png)

![GOES West Imager &#x2013; SST &#x2013; 1 month, 09/01/2018 - 09/30/2018](../.gitbook/assets/image%20%28149%29%20%281%29.png)

### Level-3 vs. Level-4 data: Puerto Rico SST

![From Irina Gladkova, NOAA/NESDIS](../.gitbook/assets/image%20%28143%29.png)

### Levels of Data: L3 -&gt; L4 examples

![From Chassot et al. 2011](../.gitbook/assets/image%20%2829%29.png)

## Near Real Time vs Science Quality

For some purposes, data is needed in near-real time \(NRT\), i.e. as quickly after being measured as possible. For many datasets, it is possible to obtain yesterday’s data \(or from a few hours ago\).

However, the processing of NRT data is a little on the “quick & dirty” side, to ensure fast through-put. To look at trends over time, or for data used in publications, Science Quality data, which has been processed more carefully for more accuracy, might be more adequate.

Different agencies have different definitions of NRT vs. Science Quality \(or Climate Quality\) data. Some science quality data are available several days after NRT, others perhaps only when the entire mission data is reprocessed.



## References

* Bruce Monger. Remote Sensing Training Program. Cornell University. 
* Robinson, Discovering the Ocean from Space. Springer. 2010
* Chassot et al. 2011. Satellite remote sensing for an ecosystem approach to fisheries management.  _ICES Journal of Marine Science_, Volume 68, Issue 4



















