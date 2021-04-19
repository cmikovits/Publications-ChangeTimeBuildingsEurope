## DATA INFORMATION

### Statistics

#### Country Overview

#### OSM vs OSM change over time

#### OSM vs CAD/CEN

### Geostatistics

Analysis on area basis:

| type                | area | horiz. |  vert. |    number |
|---------------------|------|--------|--------|-----------|
| political ( NUTS3)  |   -  |      - |      - |     1,719 |
| regular hex         |  10  |  3,924 |  3,398 | 1,887,923 |
| regular hex         | 100  | 12,408 | 10,746 |   195,053 |

Data from OSM, GHS and GUF is clipped for each  area and the following values are calculated for each dataset:

- area
- no of features 
- mean center (x,y)
- standard distance

#### Workflow:

polygons (NUTS, HEX) feature loop
1. polygon -> get OSM buildings from dataset (sjoin)
2. polygon -> bounding box points
3. get raster names
4. load raster files and merge
5. calculate zonal statistics (for raster: rasterstats)

#### GHSL S1 (Global Human Settlement Layer Sentinel1 - EU JRC)

https://ghsl.jrc.ec.europa.eu/ghs_bu_s1_2019.php

- the tif filename can be fetched from a shp - fieldname: "location"
- values: 1 = building (built up area); 0 = empty
- year: 2018
- resolution: 20m


#### GHSL S2 (Global Human Settlement Layer Sentinel2 - EU JRC)

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

https://www.dlr.de/guf

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

east and south is easy, always lower number then higher number:

```GUF04_DLR_v02_e030_s05_e035_s10_OGR04```

east and north:

```GUF04_DLR_v02_e010_n55_e015_n50_OGR04```

west and south:

```GUF04_DLR_v02_w180_s30_w175_s35_OGR04```

west and north:

```GUF04_DLR_v02_w150_n65_w145_n60_OGR06```

attention:

w000 is always e000:

```GUF04_DLR_v02_w005_n05_e000_n00_OGR04```

s00 is always n00:

```GUF04_DLR_v02_e170_n00_e175_s05_OGR04```
