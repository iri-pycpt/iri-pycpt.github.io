---
layout: page
title: "Installing PyCPT"
permalink: /installation/
order: 2
---

## Installation

PyCPT is packaged and distributed with [Anaconda](https://www.anaconda.com/products/distribution). You will need to download and install an Anaconda distribution of Python in order to use PyCPT. 

Anaconda provides a self explanatory graphical installer- an application which will guide you through the steps necessary to install the Anaconda command line interface. 

Once you have installed Anaconda open a terminal / command line application. If you're working on a MacOS machine, use the Terminal app; Windows users should use the Anaconda Prompt app, and linux users can use whichever command line application they normally use. 

If Anaconda has installed correctly, the terminal prompt will be prefaced by ```(base)```- this is the name of the default Anaconda environment. Once you have properly installed Anaconda, you can create and activate a PyCPT anaconda environment as described in the next section. 

## PyCPT Quickstart:

Download the lock file for your platform (Linux, Windows, or macOS/osx) from  https://github.com/iri-pycpt/notebooks/tree/master/Operations. For example, if using Windows, download https://github.com/iri-pycpt/notebooks/blob/master/Operations/conda-win-64.lock .

Then in an Anaconda command shell:

```
conda create -n pycpt_environment --file conda-win-64.lock
conda activate pycpt_environment
jupyter notebook
```

Once you've executed the above, a jupyter notebook interface should start in a browser- you'll be able to start a new jupyter notebook file and run it under the "pycpt_environment" kernel.

## Updating from a previous version of PyCPT

If you already have a conda environment with a working version of PyCPT installed, the safest way to upgrade to the latest version is to leave the existing environment as it is, and create a new environment using the same commands given above, but using a different environment name, e.g. `pycpt_environment2`. That way, if the new version doesn't work for you, you can continue using the previous version. Once you're satisfied that the new version works, you can save space  by removing the old environment:
```
conda env remove -n old_environment
```



