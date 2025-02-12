# patchedDEM
Patching lakes from one DEM with land from another.

### Goal

We have two DEMs: one is high-resolution LiDAR, 
but for lakes, it shows the water-surface elevation. 
The other DEM (from Minnesota Geological Survey, or MGS) 
is lower resolution, but shows lake-bottom elevation/bathymetry, 
which we want. 
We will cut out the lakes from the bathymetry DEM, 
interpolate them to a higher resolution, 
and patch them with the LiDAR.

### Data sources
Lake locations: https://gisdata.mn.gov/dataset/water-national-hydrography-data
These provide the boundaries of the regions to clip from the bathymetry DEM.

HUC8 watershed boundaries: https://gisdata.mn.gov/dataset/geos-dnr-watersheds

### Python program
#### stitchDEMs.py 
This program loops through the HUC8 sub-watersheds. 
Inside each sub-watershed, it filters the lake dataset 
to find which lakes are inside that watershed.
It then interpolates the MGS DEM across the lake boundaries
to achieve a resolution of 1m. Then, it patches the interpolated
lake with the LiDAR for the rest of the sub-watershed.
There is an option to output some of these intermediate steps
for testing purposes.

#### viewInterpolation.py
This program plots the intermediate files from
above. It shows the LiDAR and the MGS DEM individually,
and the patched DEM.