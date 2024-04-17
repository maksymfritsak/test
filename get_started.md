## Supported Platforms: Windows, MacOS, Linux

# Available Data Types
RAD supports both DICOM and NIfTI input file formats, facilitating diverse medical imaging workflows.

## DICOM: 
Each patient's folder should contain exactly one DICOM series and not more than one RTstruct file.
Rad supports only files with DICOM Modality tag (0008, 0060) equals CT, PT, MR, or RTSTRUCT.

* **CT**: RAD assumes that CT is already provided in Hounsfiled Units.

* **PT**: RAD calculates the SUV with the body weight strategy. For this the following DICOM tags should be present: Radiopharmaceutical Start Time (0018,1072), Decay Correction (0054,1102), Decay Factor (0054,1321), Radionuclide Half Life (0018,1075), Series Time (0008,0031), and Patient's Weight (0010,1030).

* **MR**: RAD reads raw 3D image from the DICOM array without any preprocessing.

## NIfTI:
RAD handles both `.nii` and `.nii.gz` file formats.

* **CT, MR, PT**: All necessary data conversions are assumed to be pre-handled (CT is already converted to HU and PET is already converted to SUV); RAD will only read the raw 3D image.

# Preparing Your Data
## Organizing Patient Data:
* Locate all patient folders into a single directory;
* RECOMMENDED: Rename patient folders using integers (e.g., 1, 14, 325) for simplicity. Avoid special symbols or letters;
* Each folder should represent a single patient with a single image inside.

## Standardizing Structure Names:
* Ensure consistency in the naming of studied structures across all patients. For example, in a study of the prostate CTV across 150 patients, each patient should have an identically named structure, e.g., `prostate_CTV`. Avoid variations like `PROSTATE_CTV` or `prostate_1`, as these are assumed to represent different ROIs.

## File Naming Conventions for NIfTI:
* Maintain the same file name for the patient's image (e.g. 'image.nii.gz'). The image file name should be identical among the studied patients.
