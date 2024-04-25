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
* **structure_set (list[str])**: List of structure names from which to extract radiomics.

  **Example**: `structure_set=['lung', 'liver', 'CTV']`;

  **Optional**: For DICOM input data type use `['ExtractAllMasks']` to include all structures in the RTstruct file;

* **aggr_dim (str) {'2D', '2.5D', '3D'}, default='3D'**: Single volume (3D) feature extraction, slice-wise (2D), or direction-slice-wise (2.5D);
* **aggr_method (str) {'MERG', 'AVER', 'SLICE_MERG', 'DIR_MERG'}, default='AVER'**: Different feature agregation methods. See the ??? guide for more details;

  **Note!** Only the following 6 combinations are allowed:

  * `aggr_dim`='2D' and `aggr_method`='AVER';

  * `aggr_dim`='2D' and `aggr_method`='SLICE_MERG';
  
  * `aggr_dim`='2.5D' and `aggr_method`='DIR_MERG';

  * `aggr_dim`='2.5D' and `aggr_method`='MERG';
    
  * `aggr_dim`='3D' and `aggr_method`='AVER';

  * `aggr_dim`='3D' and `aggr_method`='MERG'.
  
* **intensity_range (list[float], list[int] or None), default=None**: If non-`None`, voxels with intensities outside the provided `intensity_range` are excluded from the intensity ROI mask.

  **Example**: `intensity_range = [-1000, 500]`.

* **outlier_range (float, int, or None), default=None**: In $\sigma$. If non-`None`, voxels that are not in the range [ $\mu$ - `outlier_range` $\times\sigma$, $\mu$ + `outlier_range` $\times\sigma$] are excluded from the intensity ROI mask.
* **number_of_bins (int or None), default=None**: If non-`None`, intensities within ROI are discretised to a fixed number of bins;
* **bin_size (float, int, or None), default=None**: If non-`None`, a bin is assigned for every intensity interval, interval length is a `bin_size`;

  **Note!** Simultaneously only one of two binning strategies `number_of_bins` or `bin_size` should be non-`None`. Being both `None` or both non-`None` is not supported.

* **slice_weighting (bool), default=False**: If `aggr_dim`='2D' and `slice_weighting` set to True, for texture features, the weighting is proportional to the number of voxels in ROI in the slice;
* **slice_median (bool), default=False**: If `aggr_dim`='2D' and `slice_weighting` set to True, for texture features, instead of averaging performed median selection;

  **Note 1**: Configuration where both `slice_weighting` and `slice_median` are True is not supported;
  
  **Note 2**: Configuration where both `slice_weighting` and `slice_median` are False - averaging of features performed.
  
* **start_folder, stop_folder (int or None), default=None**: Define a range of folders to process;

  **Important**: If both `start_folder` and `stop_folder` are non-`None`, than **ALL** folder names inside the `load_dir` must be integers;

* **list_of_patient_folders (list[str] or None), default=None**: Specify folders to process, allowing any symbols or letters in folder names;

   **NOTE 1**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are `None` then Z-Rad will take all folders from the `load_dir`;
  
   **NOTE 2**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are non-`None` then Z-Rad will take all folders from the `list_of_patient_folders`.

* **nifti_image (str or None), default=None**: If the data type is NIFTI, specify the name of the NIFTI image file, including the extension;

  **Example**: `nifti_image='image.nii.gz'`.

* **number_of_threads (int), default=1**: Number of threads for parallel processing. Consider the machine's RAM limits.

## Methods:

* **extract_radiomics()**: performs radiomics calculation based on provided information and saves the .xlsx to the `save_dir`.


## Examples:

### IBSI I Config. A (NIFTI):

* Studied structure: mask;
* NIfTI image: phantom.nii.gz;
* Slice-wise (2D) feature extraction;
* Intensity range: [-500, 400];
* Fixed bin size: 25.

Here we perform only 'MERG' method.

```python
rad = Radiomics(load_dir='Test_Cases/IBSI I/NIFTI/', 
                save_dir='Test_Cases/IBSI I/Save/A_NIFTI',
                input_data_type='NIFTI', 
                input_imaging_mod='CT',
                intensity_range=[-500, 400], 
                bin_size=25, 
                aggr_dim='2D', 
                aggr_method='MERG',
                list_of_patient_folders=['1'],
                structure_set=['mask'],
                nifti_image='phantom.nii.gz',
                number_of_threads=1)
rad.extract_radiomics()
```

### IBSI I Config. A (DICOM):

* Studied structure: GTV-1;
* Slice-wise (2D) feature extraction;
* Intensity range: [-500, 400];
* Fixed bin size: 25.

Here we perform only 'MERG' method.

```python
rad = Radiomics(load_dir='Test_Cases/IBSI I/DICOM/', 
                save_dir='Test_Cases/IBSI I/Save/A_DICOM',
                input_data_type='DICOM', 
                input_imaging_mod='CT',
                intensity_range=[-500, 400], 
                bin_size=25, 
                aggr_dim='2D', 
                aggr_method='MERG',
                list_of_patient_folders=['1'],
                structure_set=['GTV-1'], 
                number_of_threads=1)
rad.extract_radiomics()
```
