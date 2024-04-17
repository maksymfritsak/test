# Prerequisites
Ensure the following before starting:
* **Recommended Python Version:** 3.11
* **Supported Platforms:** Windows, MacOS, Linux

# Available Data Types
RAD supports both DICOM and NIfTI input file formats, facilitating diverse medical imaging workflows.

## DICOM
Each patient's folder should contain exactly one DICOM series and not more than one RT structure file.
Rad supports only files with DICOM tag (0008, 0060) Modality equals CT, PT, MR, or RTSTRUCT.

### CT
RAD assumes that CT is already provided in Hounsfiled Units.

### PT
RAD calculates the SUV with the body weight strategy. For this DICOM tags () should be present.

### MR
RAD reads raw 3D array from the DICOM.

## NIfTI
RAD handles both `.nii` and `.nii.gz` file formats efficiently.

### CT, MR, PT
All necessary data conversions are assumed to be pre-handled (CT is already converted to HU and PET is already converted to SUV); RAD will only read the raw 3D data arrays.

# Preparing Your Data
## Organizing Patient Data
* Organize all patient folders into a single directory. 
* RECOMENDED: Rename patient folders using integers (e.g., 1, 14, 325) for simplicity. Avoid special symbols or letters.
* Each folder should represent a single patient with a single image inside.

## Standardizing Structure Names
* Ensure consistency in naming the studied structures across all patients. For example, if studying the left lung, name it `lung_left` consistently in every patient folder. Variations such as `Lung_left` or `LUNG_left` will be treated as distinct structures.
* For a study involving radiomics extracted from the prostate CTV across 150 patients, each should have a similarly named structure, e.g., `prostate_CTV`. Avoid variations like `PROSTATE_CTV` or `prostate_1`, as these are assumed to represent different regions of interest (ROIs).

## File Naming Conventions for NIfTI
* Maintain the same file name for the patient image e.g. 'image.nii.gz'. Image file mane should be identical among the studied patients.
