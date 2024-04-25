---
layout: default
theme: architect
---

# Filtering

First of all, one needs to design a filter and then implement it to the data.

## Mean Filter:
>class Mean(padding_type, support, dimensionality)

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: Different strategies for handling boundary voxels. For more detailed information consult the [Filtering](filtering.md);
* **support (int)**: Filter size (in the number of voxels);
* **dimensionality (str) {'2D', '3D'}**: If '3D' - filter applied as a qube to the 3D image, '2D' - filter applied as a square to each slice. 

## Laplacian of Gaussian:

>class LoG(padding_type, sigma_mm, cutoff, dimensionality):

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: Different strategies for handling boundary voxels. For more detailed information consult the [Filtering](filtering.md).
* **sigma_mm (int, float)**: Standard deviation of the Gaussian blur (controls the scale of the blur);
* **cutoff (int, float)**: The threshold used to determine significant edges after the LoG filter has been applied;
* **dimensionality (str) {'2D', '3D'}**: If '3D' - filter applied as a qube to the 3D image, '2D' - filter applied as a square to each slice. 
  
## Laws Kernels:

>class Laws(response_map, padding_type, distance, energy_map, dimensionality, rotation_invariance=False, pooling=None)

* **response_map (str)**:
* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: Different strategies for handling boundary voxels. For more detailed information consult the [Filtering](filtering.md);
* **distance (int)**:
* **energy_map (bool)**:
* **dimensionality (str) {'2D', '3D'}**: '3D' - filter applied as a qube to the 3D image; '2D' - applied as a square to each slice
* **rotation_invariance (bool)**: '3D' - filter applied as a qube to the 3D image; '2D' - applied as a square to each slice.
* **pooling**: 

## Wavelets:

### 2D

>class Wavelets2D(wavelet_type, padding_type, response_map, decomposition_level, rotation_invariance=False)

* **wavelet_type (str) {'db3', 'db2', 'coif1', 'haar'}**: Avaliable wavelet filters.
* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: Different strategies for handling boundary voxels. For more detailed information consult the [Filtering](filtering.md);
* **response_map (str) {'LL', 'HL', 'LH', 'HH'}**:
* **decomposition_level (int) {1,2}**:
* **rotation_invariance (bool), default=False**:

### 3D

>class Wavelets3D(wavelet_type, padding_type, response_map, decomposition_level, rotation_invariance=False)

* **wavelet_type (str) {'db3', 'db2', 'coif1', 'haar'}**: Avaliable wavelet filters.
* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**: Different strategies for handling boundary voxels. For more detailed information consult the [Filtering](filtering.md);
* **response_map (str) {'LLL', 'LLH', 'LHL', 'HLL', 'LHH', 'HHL', 'HLH', 'HHH'}**:
* **decomposition_level (int) {1,2}**:
* **rotation_invariance (bool), default=False**:
