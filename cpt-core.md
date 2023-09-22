---
layout: page
title: CPT-CORE
permalink: /cpt-core/ 
---

## CPT-CORE 

CPT-CORE is the analytical engine of PyCPT- it manages the input and output of CPT in such a way that the user never has to deal with output files or bash scripting, if they don't want to.

A functional API is the core of CPT-CORE. This is a set of Python functions which implement entire CPT workflows at once. 

```cptcore.canonical_correlation_analysis(X, Y, F=F, **kwargs)``` is a function which implements CPT's CCA bias-correction. New settings have been added, when compared to legacy PyCPT, including SPI, Anomalies, and Y-Transformations. 

```cptcore.principal_components_regression(X, Y, F=F, **kwargs)``` is a function which implements CPT's PCR bias-correction. 


```cptcore.multiple_linear_regression(X, Y, F=F, **kwargs)``` is a function which implements CPT's MLR bias-correction. 


```cptcore.deterministic_skill(X, Y, **kwargs)``` is a function which implements CPT's deterministic skill scores. 


```cptcore.probabilistic_forecast_verification(X, Y, **kwargs)``` is a function which implements CPT's probabilistic skill scores. 




## More Detail: 

#### Base CPT Class: 
```
class CPT:
    def __init__(self, interactive=False,  log=None, project_file=None,  record=None, output_files=default_output_files, outputdir=None, **kwargs):
```
interactive - whether to print CPT's stdout to the python terminal 
log - file to save log of CPT activity to
project file - file to save inputs from user to CPT for the record 
record - record of CPT outputs 
output_files - a dict indicating where to save which files - keys need to conform to the keys in ```cptcore.default_output_files.keys()``` 
outputdir - directory to save files in


#### CCA: 
```
def canonical_correlation_analysis(
        X,  # Predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        Y,  # Predictand Dataset in an Xarray DataArray with three dimensions, XYT 
        F=None, # New Out of sample (forecast) predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        transform_predictand=None,  # transformation to apply to the predictand dataset - None, 'Empirical', 'Gamma'
        tailoring=None,  # tailoring None, Anomaly, StdAnomaly, or SPI (SPI only available on Gamma)
        cca_modes=(1,5), # minimum and maximum of allowed CCA modes 
        x_eof_modes=(1,5), # minimum and maximum of allowed X Principal Componenets 
        y_eof_modes=(1,5), # minimum and maximum of allowed Y Principal Components 
        crossvalidation_window=5,  # number of samples to leave out in each cross-validation step 
        retroactive_initial_training_period=0.45, # percent of samples to be used as initial training period for retroactive validation
        retroactive_step=0.1, # percent of samples to increment retroactive training period by each time. 
        validation='crossvalidation', #type of leave-n-out crossvalidation to use
        synchronous_predictors=False,
        cpt_kwargs={}, # a dict of kwargs that will be passed to CPT 
        x_lat_dim=None, 
        x_lon_dim=None, 
        x_sample_dim=None, 
        x_feature_dim=None, 
        y_lat_dim=None, 
        y_lon_dim=None, 
        y_sample_dim=None, 
        y_feature_dim=None, 
        f_lat_dim=None, 
        f_lon_dim=None, 
        f_sample_dim=None, 
        f_feature_dim=None, 
    ): -> Hindcasts, Forecasts, Skill, Patterns(X), Patterns(Y) 
```

#### PCR: 
```
def principal_components_regression(
        X,  # Predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        Y,  # Predictand Dataset in an Xarray DataArray with three dimensions, XYT 
        F=None, # New Out of sample (forecast) predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        crossvalidation_window=5,  # number of samples to leave out in each cross-validation step 
        transform_predictand=None,  # transformation to apply to the predictand dataset - None, 'Empirical', 'Gamma'
        tailoring=None,  # tailoring None, Anomaly, StdAnomaly, or SPI (SPI only available on Gamma)
        x_eof_modes=(1,5), # minimum and maximum of allowed X Principal Componenets 
        cpt_kwargs={}, # a dict of kwargs that will be passed to CPT 
        retroactive_initial_training_period=0.45, # percent of samples to be used as initial training period for retroactive validation
        retroactive_step=0.1, # percent of samples to increment retroactive training period by each time. 
        validation='CROSSVALIDATION', #type of leave-n-out crossvalidation to use
        synchronous_predictors=False,
        x_lat_dim=None, 
        x_lon_dim=None, 
        x_sample_dim=None, 
        x_feature_dim=None, 
        y_lat_dim=None, 
        y_lon_dim=None, 
        y_sample_dim=None, 
        y_feature_dim=None, 
        f_lat_dim=None, 
        f_lon_dim=None, 
        f_sample_dim=None, 
        f_feature_dim=None, 
    ):  -> Hindcasts, Forecasts, Skill, Patterns(X) 
```

#### MLR: 
```
def multiple_regression(
        X,  # Predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        Y,  # Predictand Dataset in an Xarray DataArray with three dimensions, XYT 
        F=None, # New Out of sample (forecast) predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        crossvalidation_window=5,  # number of samples to leave out in each cross-validation step 
        transform_predictand=None,  # transformation to apply to the predictand dataset - None, 'Empirical', 'Gamma'
        tailoring=None,  # tailoring None, Anomaly, StdAnomaly, or SPI (SPI only available on Gamma)
        cpt_kwargs={}, # a dict of kwargs that will be passed to CPT 
        retroactive_initial_training_period=0.45, # percent of samples to be used as initial training period for retroactive validation
        retroactive_step=0.1, # percent of samples to increment retroactive training period by each time. 
        validation='crossvalidation', #type of leave-n-out crossvalidation to use
        regression='OLS',
        link='identity',
        synchronous_predictors=False,
        x_lat_dim=None, 
        x_lon_dim=None, 
        x_sample_dim=None, 
        x_feature_dim=None, 
        y_lat_dim=None, 
        y_lon_dim=None, 
        y_sample_dim=None, 
        y_feature_dim=None, 
        f_lat_dim=None, 
        f_lon_dim=None, 
        f_sample_dim=None, 
        f_feature_dim=None, 
    ): -> hindcasts, forecasts, skill
```

#### Deterministic Skill
```
def deterministic_skill(
        X,  # Predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        Y,  # Predictand Dataset in an Xarray DataArray with three dimensions, XYT 
        synchronous_predictors=False,
        cpt_kwargs={}, # a dict of kwargs that will be passed to CPT 
        x_lat_dim=None, 
        x_lon_dim=None, 
        x_sample_dim=None, 
        x_feature_dim=None, 
        y_lat_dim=None, 
        y_lon_dim=None, 
        y_sample_dim=None, 
        y_feature_dim=None, 
    ): -> skill
```

#### PFV:
```
def probabilistic_forecast_verification(
        X,  # Predictor Dataset in an Xarray DataArray with three dimensions, XYT 
        Y,  # Predictand Dataset in an Xarray DataArray with three dimensions, XYT 
        synchronous_predictors=False,
        cpt_kwargs={}, # a dict of kwargs that will be passed to CPT 
        x_lat_dim=None, 
        x_lon_dim=None, 
        x_sample_dim=None, 
        x_feature_dim=None, 
        y_lat_dim=None, 
        y_lon_dim=None, 
        y_sample_dim=None, 
        y_feature_dim=None, 
      
    ): -> skill
```
