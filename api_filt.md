---
layout: default
theme: architect
---

# Filtering

First of all, one needs to design a filter and then implement it to the data.

## Mean Filter
>class Mean(padding_type, support, dimensionality)

* **dimensionality (str) {'2D', '3D'}**
* **support (int)**
* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**

## Laplacian of Gaussian

>class LoG(padding_type, sigma_mm, cutoff, dimensionality):

* **dimensionality (str) {'2D', '3D'}**
* **padding_type (str) {'constant', 'nearest', 'wrap', 'reflect'}**

* **sigma_mm (int, float)**

* **cutoff (int, float)**:

## Laws Kernels

## Wavelets
