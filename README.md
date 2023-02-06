# AAAI23-Evaluating_AgriRecommendations

### Dataset Description

| **Variable** 	| **Description** 	| **Source** 	|
|---	|---	|---	|
| id 	| parcel unique identification number 	| Farmers' Cooperative 	|
| ha 	| parcel area in hectare 	| Farmers' Cooperative 	|
| variety 	| seed variety 	| Farmers' Cooperative 	|
| sdate 	| sowing date 	| Farmers' Cooperative 	|
| hdate 	| harvest date 	| Farmers' Cooperative 	|
| yield21 	| yield of 2021 in kg/ha 	| Farmers' Cooperative 	|
| lat 	| centroid of parcel 	| Farmers' Cooperative 	|
| lon 	| centroid of parcel 	| Farmers' Cooperative 	|
| field_area 	| calculated by georeferenced parcel 	| Analysis 	|
| perimeter 	| calculated by georeferenced parcel 	| Analysis 	|
| ratio 	| field_area to perimeter 	| Analysis 	|
| prediction 	| the recommendation in sowing date 	| Recommender System 	|
| HIGH 	| max ambient temperature on sowing day 	| Nearest weather station 	|
| LOW 	| max ambient temperature on sowing day 	| Nearest weather station 	|
| clay_mean 	| mean value of parcel about clay content (%) in topsoil (0-20cm) (modelled by Multivariate Additive Regression Splines) 	| European Soil Data Centre (ESDAC) of Joint Research Center 	|
| sand_mean 	| mean value of parcel about sand content (%) in topsoil (0-20cm) (modelled by Multivariate Additive Regression Splines) 	| European Soil Data Centre (ESDAC) of Joint Research Center 	|
| silt_mean 	| mean value of parcel about silt content (%) in topsoil (0-20cm) (modelled by Multivariate Additive Regression Splines) 	| European Soil Data Centre (ESDAC) of Joint Research Center 	|
| occont_mean 	| mean value of parcel topsoil organic carbon content (g C kg-1) 	| European Soil Data Centre (ESDAC) of Joint Research Center 	|
| var_code 	| seed variety code  	| Analysis 	|
| len_season 	| length of season, harvest doy minus sowing doy 	| Farmers' Cooperative 	|
| peak_ndvi 	| calculation of the peak of ndvi in the cultivation period 	| Copernicus Sentinel-2 	|
| trapezoidal_ndvi_sow2harvest 	| calculated using the trapezoidal rule between the total vegetation values between sowing and harvest date. 	| Copernicus Sentinel-2 	|
| ndwi_sowingday 	| calculation of the ndwi at sowing day 	| Copernicus Sentinel-2 	|
