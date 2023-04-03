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
In an Anaconda command shell:

```
conda create -c iri-nextgen -c conda-forge -n pycpt_environment pycpt
conda activate pycpt_environment
jupyter notebook
```

Once you've executed the above, a jupyter notebook interface should start in a browser- you'll be able to start a new jupyter notebook file and run it under the "pycpt_environment" kernel.

The meaning of the arguments of `conda create` are as follows:

- `-c iri-nextgen -c conda-forge`: look for packages in the `iri-nextgen` and `conda-forge` [channels](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/channels.html). Without these options, the pycpt package and its dependencies would not be found, because they haven't been published to Anaconda's main channel.
- `-n pycpt_environment`: specifies the name of the new conda environment you are creating. If an environment with that name already exists, you will be prompted to delete it first. Use a different name for the new environment if you want to keep the old one as a backup.
- `pycpt`: the name of a package to install in the new environment. All of that package's dependencies will also be installed.

## Updating from a previous version of PyCPT

If you already have a conda environment with a working version of PyCPT installed, the safest way to upgrade to the latest version is to leave the existing environment as it is, and create a new environment using the same commands given above, but using a different environment name. That way, if the new version doesn't work for you, you can continue using the previous version. Once you're satisfied that the new version works, you can save space  by removing the old environment:
```
conda env remove -n old_environment
```



