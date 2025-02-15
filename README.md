# ASPIRE-V

[![Github Actions](https://github.com/weecology/DeepForest/actions/workflows/Conda-app.yml/badge.svg)](https://github.com/weecology/DeepForest/actions/workflows/Conda-app.yml)
[![Documentation Status](https://readthedocs.org/projects/deepforest/badge/?version=latest)](http://deepforest.readthedocs.io/en/latest/?badge=latest)
[![Version](https://img.shields.io/pypi/v/DeepForest.svg)](https://pypi.python.org/pypi/DeepForest)


![img](docs/logo2.png)

ASPIRE-V (Artificial Intelligence and Space-based Monitoring for Power Lines Risk Evaluation against Vegetation) is a Python package for assessing vegetation-related risk along infrastructure lines. ASPIRE-V implements sub-modules such as
- vegetation segmentation
- tree species classification
- height estimation
- individual tree crown delineation
- tree inventory generation
- risk calculations 
- and utilities for dealing with geo-spatial data.

It is built on top of standard geo-libraries such as rasterio, geopandas, and shapely. The computer vision and machine learning modules are instead built on top of tensorflow, keras and skimage.


## Motivation

 Vegetation along the infrastructure lines is one of the major causes of outages, especially along roadways and power lines. Trees can fall after strong winds, disrupting the lines and blocking the roads. If a tree is growing too close to the power line, it might also trigger wildfires.
 Traditional approaches based on visual inspections are extremely time-consuming and very costly.
 
 *ASPIRE-V* aims to ease the process of infrastructure monitoring, providing tools to characterize vegetation and calculate threat posing to nearby infrastructure.
  


# Installation

ASPIRE-V will be installed using pip (*TODO*)

```
pip install ASPIREv
```

# Basic usage

ASPIRE-V is designed to be very easy to use, implementing many functions "under the curtains". 
The code snippet below provides the code to segment a satellite image and detect trees, with few lines of code.

```Python
import ASPIRE-V as ges
# Initialize a tree segmenter
tree_segmenter = ges.tree_segmentation.TreeSegmenter(config_file = "tree_segmenter_config.yaml")

# Load a satellite image
SAT_image_path = "/.../image.tif"
SAT_image_input, meta_data = ges.io.open_geoTiFF(SAT_image_path)

# Build the model (no need to train it if is already provided in the configuration file)
tree_segmenter.build_model()

# Predict the tree mask
tree_map_predicted = tree_segmenter.generate_tree_map(SAT_image_input)
```


# Try demos using Jupyter Notebook

The following Jupyter notebooks show how to use VIRASS for particular tasks, explaining step by step the functions. 


## Vegetation segmentation 

<p float="left">
<img src="images/readme/tree_top.jpg" width="200"/>
<img src="images/readme/tree_segmentation.png" width="200"/>
</p>

[Code](/Block_tree_segmentation.ipynb)

## Tree species classification

[![10.1109/TGRS.2022.3210275](http://img.shields.io/badge/DOI-10.1101/2021.01.08.425840-B31B1B.svg)](https://ieeexplore.ieee.org/abstract/document/9905623)

<p float="left">
<img src="images/readme/tree_top.jpg" width="200"/>
<img src="images/readme/tree_species.png" width="200"/>
</p>

[Code](/Block_tree_species_classification.ipynb)


## 3D modeler

<p float="left">
<img src="images/readme/tree_top.jpg" width="200"/>
<img src="images/readme/nDSM.png" width="200"/>
</p>

[Code](/Block_tree_height_estimation.ipynb)


## Risk map generation

<img src="images/readme/tree_inventory_3D_2.png" width="300">

[Code](/main.ipynb) 


# Disclaimer

This library is made available under an open-science paradigm with the aspiration that it proves to be beneficial. Nevertheless, the author does not provide any assurance of its merchantability or fitness for a specific purpose.

If you have suggestions or improvements to suggest, feel free to contact me at: michele.gazzea@gmail.com




 
