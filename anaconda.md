---
layout: page
title: "Anaconda Tips"
permalink: /anaconda/
order: 3
---

## Intro to conda

Conda is an open-source package manager. It is used to download and install Python libraries and their dependencies, both compiled and pure-python.
In order to install PyCPT, you must first install conda. If you don't already have conda, download and run the [miniconda installer](https://docs.conda.io/projects/miniconda/en/latest/) for your operating system. If you're using Windows 10 or earlier and you don't know whether to use the 32-bit or 64-bit version, see the [Microsoft FAQ](https://support.microsoft.com/en-us/windows/32-bit-and-64-bit-windows-frequently-asked-questions-c6ca9541-8dce-4d48-0415-94a3faa2e13d). For Windows 11, use the 64-bit version.

If you have previously installed the full Anaconda distribution, you can use that instead of miniconda.

Once installed, conda is available on the command line. 
Note: Windows users should use the `Anaconda Prompt` terminal application -- standard `cmd.exe` will not give you the full functionality of conda. 

#### Environments

Conda uses an abstraction called an 'environment' to help the user keep track of what packages are installed where. For conda, an environment means "a set of installed command line utilities, programming languages and Python libraries". Environments are different if the packages they contain are different, or if their versions are different. You can think of an environment as, effectively, a set of installed Python libraries. 

Each environment has a name, and must be created, and then activated. When you start a Python terminal inside a given environment, you only have access to the packages that have been installed into that environment. If you create a package, but don't activate it, you won't have access to its contents. 

Conda downloads packages from one or more "channels." There is a base set of channels that are available by default, and you can enable other channels by adding them to the command line.

## Cheat Sheet: 

```
### Creating a new environment: 
conda create -n name_of_environment

### Activating an environment:
conda activate name_of_environment

### Deactivating an environment:
conda deactivate

### Installing into current environment:
conda install [-c name_of_channel] name_of_library

### Uninstalling a library in current environment:
conda uninstall name_of_library
```

## PyCPT Quickstart:

See [Installation Instructions](https://iri-pycpt.github.io/installation/)
