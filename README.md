## DATA INFORMATION

### Statistics

#### Country Overview

#### OSM vs OSM change over time

#### OSM vs CAD/CEN

### Geostatistics

Analysis on area basis:

| type                | area | horizontal | vertical | number    |
|---------------------|------|------------|----------|-----------|
| political ( NUTS3)  | var. |            |          |     1,719 |
| regular hex         |  10  | 3,924      | 3,398    | 1,887,923 |
| regular hex         | 100  | 12,408     | 10,746   |   195,053 |

Data from OSM, GHS and GUF is clipped for each  area and the following values are calculated for each dataset:

- area
- no of features 
- mean center (x,y)
- standard distance

#### Workflow:

polygons (NUTS, HEX)
-> feature loop
-> bounding box
-> selection of corresponding raster files
-> 

#### GHSL (Global Human Settlement Layer - EU JRC) S1

https://ghsl.jrc.ec.europa.eu/ghs_bu_s1_2019.php

- the tif filename can be fetched from a shp - fieldname: "location"
- values: 1 = building (built up area); 0 = empty
- year: 2018
- resolution: 20m


#### GHSL (Global Human Settlement Layer - EU JRC) S2

https://ghsl.jrc.ec.europa.eu/ghs_bu_s2_2018.php

- the tif filename can be fetched from a shp - fieldname: "location"
- values: probability from 0-100
- year: 2018
- resolution: 10m

#### ESM (European Settlement Layer - EU JRC)

https://ghsl.jrc.ec.europa.eu/download.php?ds=ESM

- the tif filename can be fetched from a shp - fieldname: "location"
- values: 0 = no data, 1 = land, 2 = water, 255 = built up
- year: 2015
- resolution: 2m


#### GUF (Global Urban Footprint - DLR)

filename:
```
GUF04_DLR_v02_
+ [e|w][aaa]_
+ [n|s][bb]_
+ [e|w][ccc]_
+ [n|s][dd]_
+ OGR04.tif
```
- aaa: 000-180 in steps of 5 degrees
- bb: 00-85 in steps of 5 degrees
- ccc: for w: aaa-5, for e: aaa+5
- dd: for n: bb-5, for s: bb+5

- values: 0 = building, 255 = empty
- resolution: 0.4 arcseconds (~12m at equator, 
