# About RAD

RAD is a tool developed to enhance research workflows by providing advanced data processing capabilities, particularly in the field of medical imaging.

---

# RAD User Manual

This user manual provides links to key sections for easy navigation and understanding of how to use RAD effectively:

- [Get Started](get_started.md) - Introduction and setup instructions.
- [Resampling](resampling.md) - Guide on how to resample images for analysis.
- [Filtering](filtering.md) - Information on applying filters to your data.
- [Radiomics](radiomics.md) - Detailed exploration of radiomic features extraction.

---

# Advanced: RAD API

For advanced usage, we recommend utilizing RAD as a Python library, which can be seamlessly integrated into your research workflow. The [RAD API documentation](api.md) includes useful examples and guides to get you started.

# How RAD Handles CT, PET, and MR Data

RAD is designed to support a wide range of medical imaging data types with specific considerations:

## DICOM

For DICOM data, RAD assumes that each patient folder contains only one DICOM series and one RT struct file.

### CT

Details on how RAD processes CT images are provided here.

## NIFTI

RAD supports both `.nii` and `.nii.gz` data formats, offering flexibility in handling NIFTI data.

# Contact Us

Should you have any questions or require further assistance, feel free to reach out via email at [example@example.com](mailto:example@example.com).
