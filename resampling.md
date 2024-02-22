---
layout: default
theme: architect
---
# RAD: Resampling

To perform resampling with RAD, navigate to the respective tab by clicking on 'Resampling' at the top-left corner of the menu.

![Alt text](f1.png")

Fill in the load directory (where the patient folders are located).

Then choose the image modality. Input start and stop folders to run all folders within the defined range, or define a list of patients instead. Define the number of threads to run resampling for multiple patients in parallel.

Define the save directory. Inside this directory, RAD will create folders with the original patient folder names where the resampled image and mask will be saved.

Specify the image data type. Define the resize resolution as a resolution to which one wants to resize, followed by the image interpolation method and resample dimension.

Currently, RAD supports nearest neighbors, linear, BSpline, and Gaussian interpolation methods for both image and mask interpolations.

When all fields are filled and comboboxes are chosen, we recommend saving the input by going to the menu and pressing 'Save Input', or simply by using the shortcut 'Ctrl+S'. Already saved input can be loaded through the menu by choosing 'Load Input' or by pressing 'Ctrl+O'.
