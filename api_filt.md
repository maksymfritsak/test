---
layout: default
theme: architect
---

# Filtering

First of all, one needs to design a filter and then implement it to the data.

## Mean Filter:
>class Mean(padding_type, support, dimensionality)

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: different strategies of handling boundary voxels. For more detailed information consult the [Filtering](filtering.md).
* **support (int)**: Filter size (in the number of voxels).
* **dimensionality (str) {'2D', '3D'}**: '3D' - filter applied as a qube to the 3D image; '2D' - applied as a square to each slice 

## Laplacian of Gaussian:

>class LoG(padding_type, sigma_mm, cutoff, dimensionality):

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: different strategies of handling boundary voxels. For more detailed information consult the [Filtering](filtering.md).
* **sigma_mm (int, float)**: Defines the standard deviation of the Gaussian blur applied to an image before computing the Laplacian. This parameter controls the scale of the blur.
* **cutoff (int, float)**:  The threshold value used to decide which edges to keep after applying the LoG filter. 
* **dimensionality (str) {'2D', '3D'}**: '3D' - filter applied as a qube to the 3D image; '2D' - applied as a square to each slice
* 
## Laws Kernels:

>class Laws(response_map, padding_type, distance, energy_map, dimensionality, rotation_invariance=False, pooling=None)

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: different strategies of handling boundary voxels. For more detailed information consult the [Filtering](filtering.md);
* **distance (int)**:
* **energy_map (bool)**:
* **rotation_invariance (bool)**: '3D' - filter applied as a qube to the 3D image; '2D' - applied as a square to each slice.
* **response_map**
* **pooling**

## Wavelets:

### 2D

>class Wavelets2D(wavelet_type, padding_type, response_map, decomposition_level, rotation_invariance=False)
