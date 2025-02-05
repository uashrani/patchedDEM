# patchedDEM
Patching lakes from one DEM with land from another.

### Goal

We have two DEMs: one is high-resolution LiDAR, but for lakes, it shows the surface elevation. The other (from the MGS) is lower resolution, but shows lake-bottom elevation/bathymetry, which we want. We will cut out the lakes from the bathymetry DEM, interpolate them to a higher resolution, and patch them with the LiDAR.

### Data sources
Lake locations: https://gisdata.mn.gov/dataset/water-national-hydrography-data
These provide the boundaries of the regions to clip from the bathymetry DEM.

HUC8 watershed boundaries: https://gisdata.mn.gov/dataset/geos-dnr-watersheds

