## MULTIDIMENSION metadata domain

We adopted the metadata format used by GDAL's NetCDF driver for all multi-dimensional data. This structure describes multidimensional data for ArcGIS. NetCDF, HDF4, HDF5 and GRIB drivers were modified to construct and return MULTIDIMENSION metadata string.

### Format:
MULTIDIMENSION is standard `name`=`value` pairs with support for attributes. Attribute entries are constructed by concatenation - `name` + `#` + `attribute`.

###### E.g.:
	air_temp#accum_type=instantaneous
    air_temp#grid_type=spatial
    air_temp#level_type=multi   
    air_temp#long_name=temperature
    air_temp#missing_value=9.9999996e+35
    air_temp#stash_code=0
    air_temp#units=K
	MD_BLACKLIST={time,lat,lon,lvl,Ak,Bk,base_date,base_time,valid_date,valid_time,forc_hrs,wrtn_date,wrtn_time}
	MD_VARIABLES={seg_type,zonal_wnd,merid_wnd,air_temp,spec_hum,vertical_wnd,pressure,geop_ht,dewpt,relhum,clwc,ciwc}


### Required:
* `MD_VARIABLES` - list of variables in dataset.
* `variable#MD_DIMS` - list of dimensions in `variable`
* `variable#MD_DIM_dimension_DEF` - array that defines size and type of dimension - {size, type}; type is based on netCDF's datatype enum.
* `variable#MD_DIM_dimension_VALUES` - array of dimension values

### Common attributes:
* `#units` - variable/dimension units (data specific string)
* `#description` - long description

Format specific entries include CF attributes in NetCDF (short_name, standard_name, etc.) and GRIB codes/attributes (center, code, etc.).

### Examples:
    Metadata (multidimension):
        DBLY#description=DBLY (layer between 2 depths below land surface)
        DBLY#units=cm
        MD_VARIABLES={SOILM@DBLY}
        SOILM@DBLY#center=Zagreb
        SOILM@DBLY#center_code=221
        SOILM@DBLY#code=86
        SOILM@DBLY#description=Soil moisture content [kg/m^2] @ DBLY (layer between 2 depths below land surface)
        SOILM@DBLY#grib_name=SOILM
        SOILM@DBLY#level=DBLY
        SOILM@DBLY#level_code=112
        SOILM@DBLY#level_description=DBLY (layer between 2 depths below land surface)
        SOILM@DBLY#MD_DIM_DBLY_DEF={4,6}
        SOILM@DBLY#MD_DIM_DBLY_LABEL={0|4,0|3,0|2,0|1}
        SOILM@DBLY#MD_DIM_DBLY_VALUES={0,1,2,3}
        SOILM@DBLY#MD_DIM_time_DEF={1,6}
        SOILM@DBLY#MD_DIM_time_VALUES={1009843200}
        SOILM@DBLY#MD_DIMS={DBLY,time}
        SOILM@DBLY#subcenter_code=221
        SOILM@DBLY#table_code=1
        SOILM@DBLY#units=kg/m^2
        time#time_origin=1009843200
        time#units=seconds since origin
