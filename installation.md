---
layout: page
title: "installation"
permalink: /installation/
---

## Installation

PyCPT is packaged and distributed with [Anaconda](https://www.anaconda.com/products/distribution). You will need to download and install an Anaconda distribution of Python in order to use PyCPT. 

Anaconda provides a self explanatory graphical installer- an application which will guide you through the steps necessary to install the Anaconda command line interface. 

Once you have installed Anaconda open a terminal / command line application. If you're working on a MacOS machine, use the Terminal app; Windows users should use the Anaconda Prompt app, and linux users can use whichever command line application they normally use. 

If Anaconda has installed correctly, the terminal prompt will be prefaced by ```(base)```- this is the name of the default Anaconda environment. Once you have properly installed Anaconda, you can create and activate a PyCPT anaconda environment, then add it as a Jupyter Kernel with these commands, at a command line: 

## PyCPT Quickstart:

```
conda create -c conda-forge -c hallkjc01 -n pycpt_environment pycpt
conda activate pycpt 
python -m ipykernel install --user --name=pycpt_environment 
jupyter notebook
```

Once you've executed the above, a jupyter notebook interface should start in a browser- you'll be able to start a new jupyter notebook file and run it under the "pycpt_environment" kernel.

You can replace "pycpt_environment" with any aribtrary environment name-  if you wanted to name it after a specific project, or something, for example, you could use ```conda create -c conda-forge -c hallkjc01 -n lac_forecasts pycpt``` instead. ```pycpt``` is the name of the package - if you wanted additional packages, you could add them on the end, like this: 

```
conda create -c conda-forge -c hallkjc01 -n pycpt_environment pycpt xarray scikit-learn tensorflow matplotlib
```

```hallkjc01``` and ```conda-forge``` specify Anaconda [channels](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html) - just more places to look for the packages to download! More details on Anaconda environments [here](https://iri-pycpt.github.io/anaconda) 



