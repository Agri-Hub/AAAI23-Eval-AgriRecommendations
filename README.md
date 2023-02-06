# Evaluating Digital Agriculture Recommendations with Causal Inference :tractor::triangular_ruler:

In the aforementioned work we propose an observational causal inference framework for the empirical evaluation of the impact of digital tools on target farm performance indicators. As a case study, we perform an empirical evaluation of a recommendation system for optimal cotton sowing, which was used by a farmers' cooperative during the growing season of 2021. We leverage agricultural knowledge to develop the causal graph of the farm system, we use the back-door criterion to identify the impact of recommendations on the yield and subsequently we estimate it using several methods on observational data (linear regression, matching, inverse propensity score weighting and meta-learners). The results showed that a field sown according to our recommendations enjoyed a significant increase in yield (12% to 17%). 

This repository contains the code & data in order to reproduce the results of the paper either to use the code or the dataset for further experimentation.

### Causal Graph

Follows the graph of the farm system, encoding the causal relations between the relevant agro-environmental actors

<img src="https://github.com/Agri-Hub/AAAI23-Evaluating_AgriRecommendations/blob/main/images/causal_graph_final.png?raw=true" alt="parcel" width="500"/>

In the table below, variable identifier, description and source are presented for the easier interpretation of above causal graph.

| Id  | Variable Description    | Source                   |
|-----|-------------------------|--------------------------|
| T   | Treatment               | Farmers' Cooperative, RS |
| WF  | Weather forecast        | GFS, WRF                 |
| WS  | Weather on sowing day   | Nearest weather station  |
| WaS | Weather after sowing    | Nearest weather station  |
| CG  | Crop Growth             | NDVI via Sentinel-2      |
| SM  | Soil Moisture on sowing | NDWI via Sentinel-2      |
| SP  | Topsoil properties      | Map by ESDAC             |
| SoC | Topsoil organic carbon  | Map by ESDAC             |
| SV  | Seed Variety            | Farmers' Cooperative     |
| G   | Geometry of field       | Farmers' Cooperative     |
| AdS | Practices during sowing | Farmers' Cooperative     |
| AbS | Practices before sowing | Farmers' Cooperative     |
| AaS | Practices after sowing  | Farmers' Cooperative     |
| HD  | Harvest Date            | Farmers' Cooperative     |
| Y   | Outcome (Yield)         | Farmers' Cooperative     |


### Dataset [![CC BY 4.0][cc-by-shield]][cc-by]

The Agriculture Cooperative of Orchomenos collected and provided the required data for each field (i.e. geo-referenced boundaries, sowing & harvest date, seed variety, yield). We then combined this data with publicly available observations from heterogeneous sources (i.e., Sentinel-2 images, meteo measurements, soil maps) to engineer an observational dataset that enables the causal analysis.

One is able to find the observational dataset in the `data.csv` file. An extended description of dataset follows in the next table. 

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

This dataset is licensed under a [Creative Commons Attribution 4.0 International License][cc-by]. 

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg

### Dependencies

The code was developed and tested in Python 3.8.5. To install the dependencies run: 

```pip install -r requirements.txt```

### Reference

If you use somehow our work please cite this

```
@article{tsoumas2022evaluating,
  title={Evaluating Digital Agriculture Recommendations with Causal Inference},
  author={Tsoumas, Ilias and Giannarakis, Georgios and Sitokonstantinou, Vasileios and Koukos, Alkiviadis and Loka, Dimitra and Bartsotas, Nikolaos and Kontoes, Charalampos and Athanasiadis, Ioannis},
  journal={arXiv preprint arXiv:2211.16938},
  year={2022}
}
```

### Acknowledgements

We thank the Agriculture Cooperative of Orchomenos for the collaboration and data provision, and Corteva Hellas for their support. 

This research was funded by the EU H2020 program through the "EuroGEO Showcases: Applications Powered by Europe" (e-shape) project (Grant agreement ID: 820852). It was also funded by the General Secretariat for Research and Innovation (GSRI, Greece) under the Action ERANETs 2021A [Call ID: 037KE - A/A MIS 4888] (Project Number: T12ERA5-00075) and through the 2019-2020 BiodivERsA joint call for research proposals [BiodivClim ERA-Net COFUND programme].

_email contact: i.tsoumas (at) noa.gr_
