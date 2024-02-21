# Prerequirements: 
Recommended python version: 3.11;

Supported platforms: MS Windows, MacOS, and Linux.

# Avaliable Data Types

RAD is designed to support both DICOM and NiFTI as input file formats.

## DICOM: 

Each patient folder should contain only one DICOM series and one RT struct file.

### CT:

Read the image in Hounsfield Units, without intensity conversion 

### PT: 

Calculates the intensity from the SUV following one of the two strtegies depends on the data type:

### MR:

Reads raw 3D arry without any conversion

## NIFTI

RAD supports both `.nii` and `.nii.gz` data formats.

### CT, MR, PT:

For all imaging formats assumed the any neened conversion was done already, thus read only the raw 3D array.

# How to prepare your data:

Place all your patient folders into one directroy. 

Paient folders should be renamed as integers (e.g. 1, 14, 325, etc.), without any specials symbols or letters. 

Each patient folder should consist only one patient.

Studied structures shold have the same name among all studied patients. 

z.B. If one studies radiomics extructed from prostate CTV for 150 patients, for each patient there should be present a structure called called sinilary e.g. 'prostate_CTV'. Wariations (e.g. PROSTATE_CTV, prostate_1, etc.) are not alowed and will be ommited.


For Nifti: all image files should have the same name among all the studied patients. Zrad would crush otherwiese 
