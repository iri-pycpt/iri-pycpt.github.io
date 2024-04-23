---
layout: page
title: "Installing PyCPT 2.8.2"
permalink: /installation/
order: 2
---

## Installation

In order to install PyCPT you will first need to install a software package management tool called conda. If you don't have conda yet, see our [conda page](anaconda.md).

Once you have installed conda, open a terminal (command line application). If you're working on a MacOS machine, use the Terminal app; Windows users should use the Anaconda Prompt app, and linux users can use whichever command line application they normally use. 

If conda has installed correctly, the terminal prompt will be prefaced by ```(base)```- this is the name of the default conda environment. Once you have properly installed conda, you can create and activate a PyCPT conda environment as described in the next section. 

## PyCPT Quickstart:

Download the notebook ([seasonal](https://github.com/iri-pycpt/notebooks/releases/download/v2.8.2/pycpt-operational.ipynb) or [subseasonal](https://github.com/iri-pycpt/notebooks/releases/download/v2.8.2/pycpt-s2s.ipynb)), as well as the conda environment file for your platform:

- [Windows](https://github.com/iri-pycpt/notebooks/releases/download/v2.8.2/conda-win-64.lock)
- [Linux](https://github.com/iri-pycpt/notebooks/releases/download/v2.8.2/conda-linux-64.lock)
- [Mac](https://github.com/iri-pycpt/notebooks/releases/download/v2.8.2/conda-osx-64.lock)

and move the two files (notebook and environment file) to your working directory.

Then in an Anaconda command shell, substituting the name of the conda environment file downloaded in the previous step:

```
conda create -n pycpt-2.8.2 --file conda-win-64.lock
conda activate pycpt-2.8.2
jupyter notebook
```

Once you've executed the above, a Jupyter Notebook interface should start in a browser. Open the notebook file (pycpt-operational.ipynb) in the Jupyter Notebook inteface

## Updating from a previous version of PyCPT

If you already have a conda environment with a working version of PyCPT installed, the safest way to upgrade to the latest version is to leave the existing environment as it is, and create a new environment using the same commands given above, but with the new version number. That way, if the new version doesn't work for you, you can continue using the previous version. Once you're satisfied that the new version works, you can save space  by removing the old environment:
```
conda env remove -n pycpt-2.5.0
```



