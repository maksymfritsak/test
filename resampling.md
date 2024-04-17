---
layout: default
theme: architect
---

# RAD: Resampling

## Accessing the Resampling Tab

To perform resampling with RAD, click on the `Resampling` tab located in the menu at the top-left corner.

![Data Preparation Example](f1.png "Example Data Preparation")

## Setting Up Directories

Specify the **load directory** (the directory containing patient folders) by either:
- Clicking on `Load Directory` and navigating to the folder.
- Copying the directory path into the field to the right of the 'Load Directory' button.

Use the same approaches to choose the **save directory** (the directory where resampled images and masks will be saved). 
Each patient will be saved in a subfolder named after the original folder.
RAD will automatically create the provided directory if it does not exist.

### Imaging Modality
Select the imaging modality (supported options: PET, CT, and MR). For details on how RAD processes each modality, refer to the [Get Started](get_started.md) guide.

## Select Patient Folders
Options to specify patient folders include:
1. Input `start` and `stop` folders to run all folders within the specified range, keeping the `patient folder list` blank (Note: **ALL** folder names in the load directory should be integers).
2. Define a specific `list of patient folders` without using `start` and `stop` folders (Note: folders can include symbols and letters).
3. Leave the `patient folder list`, `start`, and `stop` folders blank; RAD will process all folders in the provided load directory. (Note: folders can include symbols and letters).

## Processing
- Select the number of threads for parallel processing. Rad calculates one patient at one thread at a time. Keep in mind the RAM limits of your machine.

## Configuring Resampling Options

### Image Data Type
- **For DICOM**: Specify the studied structures list by typing your ROIs separated by commas. Use `ExtractAllMasks` to use all masks in the RTstruct file. Optionally, save DICOM data as NIFTI without resampling by ticking the corresponding checkbox.
- **For NIFTI**: Specify the NIfTI structure files list by typing the file names separated by commas, **excluding** the file extension. Specify the NIfTI image **including** the file extension.

### Image and Masks Resampling
- Define the resample resolution (in mm) - a resolution to which the image and masks will be resampled;
- Choose an image interpolation method (popular options include Linear and BSpline);
- Choose a mask interpolation method (popular options are Nearest Neighbors (NN) and Linear with a default threshold of 0.5).
- Choose resample dimension: 3D isotropic resampling or 2D anisotropic resampling (in-plane resampling, while keeping the original spacing in the z-direction).

## Optional Steps
- **Save Input**: Save your configuration by going to the `File ` menu and clicking `Save Input`, or using the shortcut 'Ctrl+S'.
- **Load Input**: Load a previously saved configuration by navigating to the `File` menu and selecting `Load Input` or pressing 'Ctrl+O'.
## Run the Configuration
When all fields are filled, click the `RUN` button and monitor the resampling progress in the console.
