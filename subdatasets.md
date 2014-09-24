##Changes to subdataset handling

### Slicing:

GDAL usually creates a subdataset per variable and maps dimension to bands. But the Esri branch changes this such that dimensions are sliced into subdatasets. This allows us to directly open specific dimension within a variable by using URLs.

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
    Subdatasets:
        GRIB:"GLDAS_NOAH025_M.A200201.001.2014034163602.pss.grb":1
        GRIB:"GLDAS_NOAH025_M.A200201.001.2014034163602.pss.grb":2
        GRIB:"GLDAS_NOAH025_M.A200201.001.2014034163602.pss.grb":3
        GRIB:"GLDAS_NOAH025_M.A200201.001.2014034163602.pss.grb":4