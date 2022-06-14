---
layout: page
title: About
permalink: /
order: 1
---

## PyCPT: The Python Interface to the Climate Predictability Tool (CPT)

PyCPT is a set of python libraries designed to interface with CPT to facilitate operational climate forecasting and research in Python. It is the principal tool used to implement the IRI's "NextGen" approach to climate forecasting in partner countries around the world. In version two, PyCPT has been re-designed from the ground up, and packaged with Anaconda to lower the barriers to Python climate forecasting. 

PyCPT is traditionally implemented in a ```Juypter Notebook```, which allows the user to visualize variables and data structures dynamically, and run code one step at a time. PyCPT Legacy could not be decoupled from ```Jupyter Notebook``` since it relied on ```ipython``` system commands. PyCPT version 2 is pure-python (except for CPT, of course), fully modular, and fully portable. Since it implements several things that might be very useful by themselves (downloading climate data, reading CPTv10 formatted files, running statistical analyses with CPT), these functionalities have been decoupled from on another and implemented as stand-alone python libraries in their own rights. The component libraries are: 

#### CPT-IO 

[CPT-IO](https://iri-pycpt.github.io/cpt-io) is a library designed to bridge the gap between CPT data analysis and Python data analysis, by reading and writing CPTv10-formatted TSV files. 

#### CPT-DL
[CPT-DL](https://iri-pycpt.github.io/cpt-dl) is a library designed to take the legacy "pycpt dictionary" to the next level. It implements a hard versioning system for data library download template URLs, DLAuth utilities, and pure-python download functionality. 

#### CPT-CORE 

[CPT-CORE](https://iri-pycpt.github.io/cpt-core) is a library which wraps and abstracts out the CPT fortran executable entirely. It eliminates the need for the user to struggle with compiling CPT, and turns it into an intuitive "functional API". It also provides lower-level support for customizing CPT workflows. 



#### Acknowledgments: 

PyCPT development is funded in part by: 
 - Columbia World Projects - ACToday
 - World Bank - AICCRA 

GCM Data Cataloging is funded in part by: 
 - The North American Multi-Model Ensemble (NMME) Project
 - SubX
 - S2S

#### Lead Engineer & Designer: [Kyle Joseph Chen Hall](https://kjhall01.github.io/) 





