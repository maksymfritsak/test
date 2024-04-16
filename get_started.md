# Prerequisites
Ensure the following before starting:
* **Recommended Python Version:** 3.11
* **Supported Platforms:** Windows, MacOS, Linux

# Available Data Types
RAD supports both DICOM and NIfTI input file formats, facilitating diverse medical imaging workflows.

## DICOM
Each patient's folder should contain exactly one DICOM series and one RT structure file.

### CT
RAD reads CT images in Hounsfield Units directly, without performing intensity conversion.

### PT
For PET scans, RAD calculates the SUV_bw (Standardized Uptake Value, body weight) and processes the SUV data array for further operations.

### MR
MR images are processed as raw 3D arrays, with no data conversion applied.

## NIfTI
RAD handles both `.nii` and `.nii.gz` file formats efficiently.

### CT, MR, PT
It is assumed that all necessary data conversions are pre-handled; RAD will only read the raw 3D data arrays.

# Preparing Your Data
## Organizing Patient Data
* Organize all patient folders into a single directory.
* RECOMENDED: Rename patient folders using integers (e.g., 1, 14, 325) for simplicity. Avoid special symbols or letters, and the sequence of numbers need not be consecutive.
* Each folder should represent a single patient only.

## Standardizing Structure Names
* Ensure consistency in naming the studied structures across all patients. For example, if studying the left lung, name it `lung_left` consistently in every patient folder. Variations such as `Lung_left` or `LUNG_left` will be treated as distinct structures.
* For a study involving radiomics extracted from the prostate CTV across 150 patients, each should have a similarly named structure, e.g., `prostate_CTV`. Avoid variations like `PROSTATE_CTV` or `prostate_1`, as these are assumed to represent different regions of interest (ROIs).

## File Naming Conventions for NIfTI
* Maintain uniformity in file naming across all studied patients to streamline processing.

By following these guidelines, you can optimize the configuration for RAD and ensure efficient processing of your medical imaging data.
