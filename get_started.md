# Supported platforms: 

MS Windows, MacOS, and Linux.

# Avaliable Data Types

RAD is designed to support both DICOM and NiFTI:

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

Put all your patient folders into one directroy. 

Paient folders show be nameed by integers (e.g. 1, 14, 321), without any specials symbols or letters.

Each patient folder should consist only one patient.
