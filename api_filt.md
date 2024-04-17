---
layout: default
theme: architect
---

# Filtering

First of all, one needs to design a filter and then implement it to the data.

## Mean Filter:
>class Mean(padding_type, support, dimensionality)

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**
* **support (int)**
* **dimensionality (str) {'2D', '3D'}**

## Laplacian of Gaussian:

>class LoG(padding_type, sigma_mm, cutoff, dimensionality):

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**
* **sigma_mm (int, float)**
* **cutoff (int, float)**:
* **dimensionality (str) {'2D', '3D'}**
* 
## Laws Kernels:

>class Laws(response_map, padding_type, distance, energy_map, dimensionality, rotation_invariance=False, pooling=None)

* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**
* **distance (int)**:
* **energy_map (bool)**:
* **rotation_invariance (bool)**:
* response_map
* pooling

## Wavelets:
### 2D
>class Wavelets2D(wavelet_type, padding_type, response_map, decomposition_level, rotation_invariance=False)
