- [Pull Request](#pull-request)
- [BridgeGenerator](#bridgegenerator)
  - [Definition](#definition)
  - [Code Structure](#code-structure)
  - [Package](#package)
    - [Member](#member)
      - [member's attributes](#members-attributes)
      - [member's methods](#members-methods)
    - [Component](#component)
    - [Bridge](#bridge)
  - [Tutorial](#tutorial)

# Pull Request
Fork the origin repo, and then make some changes, finally submit a pull request.

# BridgeGenerator

## Definition
In our definition, 
* [**Member**](BridgeGenerator/Member) is the basic structure part with some basic shapes, e.g. rectangle, circle, or I-shape. **(TBD)**
* [**Component**](BridgeGenerator/Component) can be simply divided into four major types -- superstructure, substructure, deck and surface feature. Each of them can be assembled by the basic members. **(TBD)**
* [**Bridge**](BridgeGenerator/Bridge) is the assemble of different components, which should be in the form of real bridge. **(TBD)**

## Code Structure
``` bash
├── BridgeGenerator
│   ├── Bridge
│   │   ├── __init__.py
│   │   └── bridge.py
│   ├── Components
│   │   ├── __init__.py
│   │   └── components.py
│   ├── Member
│   │   ├── __init__.py
│   │   ├── cfg.py
│   │   ├── member.py
│   │   └── utils.py
│   ├── __init__.py
│   ├── main.py
│   ├── test_chj.py
│   └── test_rwh.py
```

## Package
### Member
In [member.py](BridgeGenerator/Member/member.py), the superclass ```Member``` is defined as an abstract class that represents the common attributes and methods of each concrete "member".
#### member's attributes


We use cfg to define the name and shape of each different shape. The cfg file should be a dictionary with the following format.
```python
cfg = {
    'name': xxx,
    'shape': {
        'detail1': ,
        'detail2': ,
        ...
    }
}
```
As an example, the configuration for rectangle is
```python
rectangle_cfg = {
    'name': rectangle,
    'shape': {
        'Flange length': 2,
        'Web length': 1,
    }
}
```
The other attributes are given in the table.

Attribute|Data Type|Description
:-:|:-:|:-:
`name` | `str` |The name of the shape.
`shape`| `dict` |A dictionary that includes all the parameters of the shape.
`yz`|`2d numpy.ndarray`|The coordination of one cross-section for the shape in the yz-plane.
`faces`||The collection of the faces of the object.
`vertices`||The collection of the vertices of the object.
`cs_num`||The number of cross-sections.
`translation`||The translation for the cross-sections.
`rotation`||The rotation for the cross-sections.
`npts`|`int`|The number of points in one cross-section.
`obj`|`bpy.types.Object`|The corresponding blender object with the specific shape.

#### member's methods

Methods|Usage
:-:|:-:
`showCrossSection()`|An helper method returns the cross-sectional view of the object
`createObj(name)`|Create a blender object with the input `name`.
**should be some get and set methods here ...**|
### Component

### Bridge

## [Tutorial](BridgeGenerator/tutorial.md)

## Citation
If you find our work helpful to your research. Please consider citing our paper.
@article{CHENG2024100098,
title = {Random bridge generator as a platform for developing computer vision-based structural inspection algorithms},
journal = {Journal of Infrastructure Intelligence and Resilience},
volume = {3},
number = {2},
pages = {100098},
year = {2024},
issn = {2772-9915},
doi = {https://doi.org/10.1016/j.iintel.2024.100098},
url = {https://www.sciencedirect.com/science/article/pii/S2772991524000173},
author = {Haojia Cheng and Wenhao Chai and Jiabao Hu and Wenhao Ruan and Mingyu Shi and Hyunjun Kim and Yifan Cao and Yasutaka Narazaki},
keywords = {Bridge inspection, Synthetic environment, Computer graphics, Deep learning, Visual recognition},
abstract = {Recent advances in computer vision algorithms have transformed the bridge visual inspection process. Those algorithms typically require large amounts of annotated data, which is lacking for generic bridge inspection scenarios. To address this challenge efficiently, this research designs, develops, and demonstrates a platform that can provide synthetic datasets and testing environments, termed Random Bridge Generator (RBG). The RBG produces photo-realistic 3D synthetic environments of six types of bridges randomly, automatically, and procedurally. Following relevant standards and design practice, the RBG creates random cross-sectional shapes, converts those shapes into bridge components, and assembles the components into bridges. The effectiveness of the RBG is demonstrated by producing a dataset (RBG Dataset) containing 10,753 images with pixel-wise annotations, rendered in 250 different synthetic environments. Significant diversity of the photo-realistic bridge inspection environments has been achieved, while all structural components strictly conform to the definitions derived from structural engineering documents. The use of the RBG dataset has been demonstrated by training a deep semantic segmentation algorithm with 101 convolutional layers, showing successful segmentation results for both major and minor structural components. The developed RBG is expected to enhance the level of automation in bridge visual inspection process. The Python code for RBG is made public at: https://github.com/chenghaojia2323/Random-Bridge-Generator.git.}
}

