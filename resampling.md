---
layout: default
theme: architect
---
# RAD: Resampling

To perform resampling with RAD, navigate to the respective tab by clicking on 'Resampling' at the top-left corner of the menu.

<p align="center">
  <img src="f1.png" alt="Example Data Preparation" title="Data Preparation Example"/>
</p>

Specify the load directory (the directory with patient folders). One can ither click on 'Load Directory' and navigate to the folder or copy the directory into the dedicated field to the right of the 'Load Directory' button.

<p align="center">
  <img src="f2.png" alt="Example Data Preparation" title="Data Preparation Example"/>
</p>

Choose the imaging modality (supported PET, CT, and MR, on how Rad processes each modality refer to the GetStarted).
One has three different possibilities how to specify patient folders:

1) Input start and stop folders to run all folders within the defined range and keep the list of patient folders blank (IMPORTANT! ALL patient folder names in a corresponding directory should be ONLY integers);

2) Define a list of patient folders while not specifying start and stop folders. (Folders can contain symbols and letters);

3) Leave the list of folders, start and stop folders blank, in this case, Rad will go through all folders in the provided 'Load Directory' (Folders can contain symbols and letters).

Choose the number of threads to run Rad for multiple patients in parallel. But take in mind the RAM limits of your machine!

Specify the Save Directory by cleaning the corresponding button by typing it into the dedicated field. If the directory does not exist, Rad will create it. Inside the save directory, RAD will create subfolders with the original patient folder names where the resampled image and masks will be saved.

Specify the image data type (supported DICOM and NIFTI, reed on how RAD handles both types in the GetStarted guide).

IF IMAGE DATA TYPE IS DICOM: 

 Specify the studied structures list by simply typing your ROIs with the comma separator. In case one wants to use ALL masks in the rtstruct file, one can simply type: ExtractAllMasks and all masks will be used further.

 There is also an option to just save DICOM data as NIFTI without resampling, for this tick the corresponding box. and press the 'RUN' button. 

IF IMAGE DATA TYPE IS NIFTI:
 Specify the NIfTI structure files list by typing the file names with the comma separator WITHOUT the file extension.
 Specify the NIfTI image WITH the corresponding file extension.

Define the resize resolution - the resolution of the output image, followed by the image interpolation method (most popular are Linear and BSpline interpolations) and resample dimension (3D - to resample the image in all three dimensions (isotropically) or 2D - to resample only inplane but keep the z spacing as original (anisotropically)).

Currently, RAD supports nearest neighbors, linear, BSpline, and Gaussian interpolation methods for both image and mask interpolations.

For the mask interpolation strategies the most popular are NN and Linear with a default threshold of 0.5. Note that one can change the threshold directly from GUI if needed.

When all fields are filled and combo boxes are chosen, we recommend saving the input by going to the menu and pressing 'Save Input', or simply by using the shortcut 'Ctrl+S'. Already saved input can be loaded through the menu by choosing 'Load Input' or by pressing 'Ctrl+O'.

When all fields are filled press the 'RUN' button. On the console, you should be able to track the resampling progress.
