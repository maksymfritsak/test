---
layout: default
theme: architect
---


# Radiomics Calculation:

> class Radiomics:(load_dir, save_dir, input_data_type, input_imaging_mod, structure_set,
                 aggr_dim='3D', aggr_method='AVER', intensity_range=None, outlier_range=None,
                 number_of_bins=None, bin_size=None, slice_weighting=False, slice_median=False,
                 start_folder=None, stop_folder=None, list_of_patient_folders=None,
                 nifti_image=None, number_of_threads=1)

* **load_dir (str)**: Path to the directory containing patient folders;
* **save_dir (str)**: Destination directory for saved data. RAD will create it if it does not exist;
* **input_data_type (str) {'DICOM', 'NIFTI'}**: Supported medical data types are DICOM and NIfTI. See the [Get Started](get_started.md) guide for more details;
* **input_imaging_mod (str) {'CT', 'PT', 'MR'}**: Modalities should be consistent across patients. See the [Get Started](get_started.md) guide for more details;
* **structure_set (list[str])**: List of structure names to resample.

  **Example**: `structure_set=['lung', 'liver', 'CTV']`;

  **Optional**: For DICOM input data type use `['ExtractAllMasks']` to include all structures in the RTstruct file;

* **aggr_dim (str) {'2D', '2.5D', '3D'}, default='3D'**

* **aggr_method (str) {'MERG', 'AVER', 'SLICE_MERG', 'DIR_MERG'}, default='AVER'**

* **intensity_range (list[float], list[int] or None), default=None**: If not None then voxels with intensities outside the provided `intensity_range` are excluded from the intensity ROI mask.

  **Example**: `intensity_range = [-1000, 500]`.
  
* **start_folder, stop_folder (int or None), default=None**: Define a range of folders to process.

  **Important**: ALL folder names inside the `load_dir` must be integers;

* **list_of_patient_folders (list[str] or None), default=None**: Specify folders to process, allowing any symbols or letters in folder names;

   **NOTE 1**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are None then rad will take all folders from the `load_dir`;
  
   **NOTE 2**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are not None then rad will take all folders from in the `list_of_patient_folders`.

* **nifti_image (str or None), default=None**: If the data type is NIFTI, specify the name of the NIFTI image file, including the extension.
  
  **Example**: `nifti_image='image.nii.gz`;

* **number_of_threads (int), default=1**: Number of threads for parallel processing. Consider the machine's RAM limits.
    
13) outlier_range

    Data Type: float or None

    If not None, the voxels that are outside the x sigma are excluded from the intensity mask.

14) number_of_bins

    Data Type: int or None

15) bin_size
    Data Type: float, int or None

16) slice_weighting
    Data Type: bool
    Default: False

17) slice_median
    Data Type: bool
    Default: False


## Methods:

* **extract_radiomics()**: performs radiomics calculation based on provided information and saves the .xlsx to the `save_dir`.


## Examples:
