# Prerequirements: 
* Recommended Python version: 3.11;

* Supported platforms: Windows, MacOS, and Linux.

# Avaliable Data Types

RAD is designed to support both DICOM and NIfTI input file formats.

## DICOM: 

Each patient folder should contain only one DICOM series and one RT struct file.

### CT:

Rad reads the image in Hounsfield Units, without intensity conversion. 

### PT: 

Rad calculates the SUV_bw and performs any further operations on the SUV array.

### MR:

Reads raw 3D arry without any conversion.

## NIFTI

RAD supports both `.nii` and `.nii.gz` data formats.

### CT, MR, PT:

For all imaging formats assumed that any needed conversion was done already, thus read only the raw 3D array.

# How to prepare your data:

Place all your patient folders into ONE directory (aka folder). 

For the ease of using Rad, paient folders should be renamed as integers (e.g. 1, 14, 325, etc.), without any specials symbols or letters (but numbers should not strictly follow each other.). 

Each patient folder should consist ONLY ONE patient.

Studied structures shold have the same name among all studied patients (If you study left lung, then in every patient left lung structure should have the same name e.g. lung_left. For Rad structures lung_left, Lung_left, or LUNG_left are three different structures). 

If one studies radiomics extructed from prostate CTV for 150 patients, for each patient there should be present a structure called similary e.g. 'prostate_CTV'. Variations (e.g. PROSTATE_CTV, prostate_1, etc.) are not alowed as assumed to represent different ROIs.


For NIfTI: All image files should have the same name among all the studied patients. 
