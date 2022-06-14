---
layout: page
title: "Anaconda Tips"
permalink: /anaconda/
order: 3
---

## Intro to Anaconda 

[Anaconda](https://anaconda.org) is a commonly used, open-source package manager. It is used to download and install Python libraries and their dependencies, both compiled and pure-python. 
Anaconda's command line interface (CLI) is referred to as "Conda" and is accessible, once installed through the installer available [here](https://www.anaconda.com/products/distribution), in the command line through the ```conda``` utility. 

Note: Windows users should use the ```Anaconda Prompt``` terminal application - standard cmd.exe will not give you the full functionality of Anaconda. 

#### Environments

Anaconda and Conda use an abstraction called an 'environment' to help the user keep track of what packages are installed where. For conda, an environment means "a set of installed command line utilities, programming languages and Python libraries". Environments are different if the packages they contain are different, or if their versions are different. You can think of an environment as, effectively, a set of installed Python libraries. 

Each environment has a name, and must be created, and then activated. When you start a Python terminal inside a given environment, you only have access to the packages that have been installed into that environment. If you create a package, but don't activate it, you won't have access to its contents. 

#### Adding an environment to Jupyter Notebook 

In order to use a newly-created anaconda environment in a Jupyter Notebook setting, you need to add it to Jupyter as a "kernel" (For this purpose, "kernel" is synonymous with "environment"). To do that, you need to have installed the ```ipykernel``` and ```jupyter``` python libraries within the desired environment. You must then run: 

```
python -m ipykernel install --user --name=name_of_environment
```

replacing ```name_of_environment``` with the name of the environment to be installed. Once that's done, start a jupyter notebook server by running ```jupyter notebook```, and create a juypter notebook file (.ipynb) with the newly added kernel.

## Cheat Sheet: 

```
### Creating a new environment: 
conda create -n name_of_environment

### Adding extra channels: 
conda create -c name_of_channel -n name_of_environment

### Activating an environment:
conda activate name_of_environment

### Deactivating an environment:
conda deactivate

### Installing into current environment:
conda install [-c name_of_channel] name_of_library

### Uninstalling a library in current environment:
conda uninstall name_of_library

### Upgrading libraries in current environment:
conda upgrade name_of_library``` 

### Adding an environment to jupyter notebook (requires installed libraries: jupyter, ipykernel):
python -m ipykernel install --user --name=name_of_environment

### Removing an environment from jupyter notebook:
jupyter kernelspec uninstall name_of_environment
```



## PyCPT Quickstart: 

```
conda create -c conda-forge -c hallkjc01 -n pycpt_env pycpt
python -m ipykernel install --user --name=pycpt 
jupyter notebook
``` 



