# `nz_convert_polygon_to_dggs`: Convert Polygon to DGGS

## Description


 Converts a single polygon feature to a dggs data model and stores the results as csv files.
 This function loops over attributes and stores each attributes data as well.


## Usage

```r
nz_convert_polygon_to_dggs(
  SpatialPolygonsDataFrame,
  Resolution,
  TID,
  PolygonID,
  SaveIn
)
```


## Arguments

Argument      |Description
------------- |----------------
```SpatialPolygonsDataFrame```     |     a SpatialPolygonsDataFrame Object. SRC of input file must be EPSG:4326
```Resolution```     |     the resolution of DGGS. An integer value. Higher values for large polygons takes long times to run
```TID```     |     TID value, an integer value exported from nz_convert_datetim_to_tid function
```PolygonID```     |     The unique id of polygon. it is only used to store csv file with a unique name to avoid csv overwrite
```SaveIn```     |     the directory to store csv files

## Value


 


## Examples

```   
list("", "zones = readOGR(\"ecozones.shp\")\n", "for(i in seq(1,length(zones))){\n", "  print(i)\n", "  z = zones[i,]\n", "  nz_convert_polygon_to_dggs(z,1,12,i,'D:/UserData/Majid/Desktop/PLOTS/')\n", "}\n", "library(\"nzdggs\")\n", "library(\"stampr\")\n", "data(mpb)\n", "mpb$dt <- Sys.Date()\n", "mpb$YR <- mpb$TGROUP+1996\n", "mpb$dt <- as.Date(paste(mpb$YR, '-01-01', sep=\"\"), \"%Y-%m-%d\")\n", "mpb$tid <- nz_convert_datetime_to_tid(mpb$dt, '1y')\n", "proj4string(mpb) <- '+proj=aea +lat_1=50 +lat_2=58.5 +lat_0=45 +lon_0=-126 +x_0=1000000 +y_0=0 +ellps=GRS80 +datum=NAD83 +units=m +no_defs'\n", 
    "mpb <- spTransform(mpb, CRS(\"+init=epsg:4326\"))\n", "mpb <- mpb[,c(1,6)]\n", "for(i in seq(1,length(mpb))){\n", "  z = mpb[i,]\n", "  nz_convert_polygon_to_dggs(z,20,z$tid,z$ID,\"E:\\\\home\\\\crobertson\\\\\")\n", "}\n", "\n", "DSN <- nz_init(\"NZSQL\",\"SPATIAL_SCHEMA\")\n", "nz_import_file_to_db(DSN,\"E:/home/majid/cmb/cmb.csv\",\"mpb\",\"double\",T,max_errors= 4400)\n")
 ```   