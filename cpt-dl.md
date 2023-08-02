---
layout: page
title: CPT-DL 
permalink: /cpt-dl/
order: 5
---

## CPT-DL

A python library for downloading climate model data and observations from the [IRI data library](https://iridl.ldeo.columbia.edu)

## Usage

CPT-DL stores pre-made Ingrid url templates in several python dictionaries, organized by purpose. 

```cptdl.hindcasts``` stores urls designed for accessing GCM hindcasts and CPT training data

```cptdl.observations``` stores urls designed for downloading observations data

```cptdl.forecasts``` stores urls designed for downloading individual GCM forecasts. You can view these template URLs [here](https://github.com/kjhall-iri/cpt-dl/blob/master/src/catalog.py). 



If you look closely, these templates are designed to be python "F-Strings". F-Strings were introduced in Python 3.6 and allow for the dynamic evaluation of python code during string formatting. However, dynamically evaluating f-strings **themselves** is not a simple task, so ```cptdl``` implements a function called ```cptdl.evaluate_url```. ```cptdl.evaluate_url``` accepts arbitrary keyword arguments, and inserts them dynamically into the url template provided as the first positional argument, url. 

Example: 

```
formatted_url = cptdl.evaluate_url(url, predictor_extent={'east':130, ...}, ... )
``` 

```cptdl.hindcasts```, ```cptdl.forecasts``` and ```cptdl.observations``` store urls indexed by the names of the datasets they access. For example, if one wanted CanSIPSv2 Precipitation, the key would be "CanSIPSv2.PRCP". You can view the available variables in each dictionary by typing ```cptdl.hindcasts.keys()``` into a python terminal. 

Whereas PyCPT Legacy used an external ```curl``` command to download data, ```cptdl``` uses a custom pure-python download function called ```cptdl.simple_download```, which simply downloads the provided url to the provided destination file path.  It can be used in any python context, almost like ```curl```. ```curl``` has a "feature" which allows it to download whatever is served by a website, even if its a 404 not-found message. This led PyCPT Legacy to mistakenly download Error 404 HTML pages, for example when months of data didnt exist. It would try to proceed without checking. ```cptdl``` fixes this problem. 

```
def simple_download(url, dest, verbose=False, use_dlauth=False)
```

Example: 

```
import cptdl as dl 
docspage = dl.simple_download("https://raw.githubusercontent.com/kjhall-iri/cpt-dl/master/src/utilities.py", "/Path/To/Destination/utilities/py") 
```

if use_dlauth is set to ```True```, ```cptdl``` will attempt to read  ```~/.pycpt_dlauth``` and pass it as a cookie in the request to the URL. 
You can set up DLAuth with ```cptdl``` by making an account [here](https://iridl.ldeo.columbia.edu/auth/signup), and then passing the email and password you set up to the ```cptdl.setup_dlauth("email@email.com")``` function 

Example: 

```
cptdl.setup_dlauth("pycpt.dev@gmail.com")
PASSWORD: [enter your password here- it will be invisible] 
``` 

You'll then have a ```~/.pycpt_dlauth``` file, which will be used to authenticate with the IRI data library in future requests using ```use_dlauth=True```


Since the rest of the PyCPT stack is built on top of Xarray, ```cptdl``` has a convenient function for rolling the evaluation of a template URL, the download of the file, and 
the opening of that file with ```cptio```  all in one: ```dataarray = cptdl.download(url, destfile, **kwargs)``` which returns an ```Xarray.DataArray``` with the desired data. 

```
def download(baseurl, dest, verbose=False, format='cptv10.tsv', use_dlauth=True, **kwargs)
```


Example: 

```
import cptdl as dl
import datetime as dt
template = dl.hindcasts['CanSIPSv2.PRCP']
destination_file = "cansips_prcp.tsv" 
kwargs = { 
  'fdate': dt.datetime.now(),
  'first_year': 1982, 
  'final_year': 2018, 
  'predictor_extent': {
    'east': 90,
    'west': 0, 
    'north': 90, 
    'south': 0
  }, 
  'lead_low': 1.5,
  'lead_high': 3.5, 
  'target': 'Jul-Sep',
  'filetype': 'cptv10.tsv'
}

# this returns an xarray dataarray: 
da = dl.download(template, destination_file, verbose=True, **kwargs)  # verbose controls a progressbar 

# and, if you have trouble with DLAuth setup and want to try to skip it, you can turn it off like this: 
da = dl.download(template, destination_file, use_dlauth=False, verbose=True, **kwargs)  

```
  

