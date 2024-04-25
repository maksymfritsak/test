---
layout: default
theme: architect
---


# Preprocessing:

> class Preprocessing(load_dir, save_dir, input_data_type, input_imaging_mod, structure_set=None,
                 just_save_as_nifti=False, resample_resolution=1.0, resample_dimension='3D',
                 image_interpolation_method='Linear',
                 mask_interpolation_method='Linear', mask_interpolation_threshold=.5,
                 start_folder=None, stop_folder=None, list_of_patient_folders=None,
                 nifti_image=None,number_of_threads=1)

* **load_dir (str)**: Path to the directory containing patient folders;
* **save_dir (str)**: Destination directory for saved data. Z-Rad will create it if it does not exist;
* **input_data_type (str) {'DICOM', 'NIFTI'}**: Supported medical data types are DICOM and NIfTI. See the [Get Started](get_started.md) guide for more details;
* **input_imaging_mod (str) {'CT', 'PT', 'MR'}**: Modalities should be consistent across patients. See the [Get Started](get_started.md) guide for more details;
* **structure_set (list[str] or None), default=None**: List of structure names to resample;

  **Example**: `structure_set=['lung', 'liver', 'CTV']`;

  **Optional**: For DICOM input data type use `['ExtractAllMasks']` to include all structures from the RTstruct file.
  
* **just_save_as_nifti (bool), default=False**: If set to True and the input data type is DICOM, saves the original image and selected ROIs as NIFTI files, without resampling;
* **resample_resolution (float), default=1.0**: Target resolution for the resampled image in mm;
* **resample_dimension (str), {'3D', '2D'}, default='3D'**: '3D' for isotropic resampling or '2D' for in-plane resampling with original z-spacing;
* **image_interpolation_method (str), {'NN', 'Linear', 'BSpline', 'Gaussian'}, default='Linear'**: Available resampling image array strategies;  
* **mask_interpolation_method (str), {'NN', 'Linear', 'BSpline', 'Gaussian'}, default='Linear'**: Available resampling mask array strategies;
* **mask_interpolation_threshold (float), default=0.5**: Threshold for mask interpolation in the range [0, 1]. Necessary for the 'Linear', 'BSpline', 'Gaussian' resampling strategies;
* **start_folder, stop_folder (int or None), default=None**: Define a range of folders to process.

  **Important**: If both `start_folder` and `stop_folder` are non-None, than **ALL** folder names inside the `load_dir` must be integers.

* **list_of_patient_folders (list[str] or None), default=None**: Specify folders to process, allowing any symbols or letters in folder names;

   **NOTE 1**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are `None` then Z-Rad will take all folders from the provided `load_dir`;
  
   **NOTE 2**: If `start_folder`, `stop_folder`, and `list_of_patient_folders` are not `None` then rad will take folders only from the `list_of_patient_folders`.

* **nifti_image (str or None), default=None**: If the data type is NIFTI, specify the name of the NIFTI image file, including the extension.
  
  **Example**: `nifti_image='image.nii.gz'`.

* **number_of_threads (int), default=1**: Number of threads for parallel processing. Consider the machine's RAM limits!



## Methods:

* **resample()**: performs resampling based on provided information and saves resampled data to the `save_dir`.


## Examples:

### IBSI I Config. B (NIFTI):
In this example, we perform resampling on the NIFTI phantom studied in IBSI I Configuration B.

* Studied structure: mask;
* NIfTI image: phantom.nii.gz;
* Slice-wise resampling (2D);
* Linear interpolation 2mm × 2mm (axial);
* Linear ROI interpolation;
* ROI rounding threshold 0.5.

```python
prep = Preprocessing(load_dir='Test_Cases/IBSI I/NIFTI',
                     save_dir='Test_Cases/IBSI I/Save/B_NIFTI',
                     input_data_type='NIFTI',
                     input_imaging_mod='CT',
                     structure_set=['mask'],
                     just_save_as_nifti=False,
                     resample_resolution=2.0,
                     resample_dimension='2D',
                     image_interpolation_method='Linear',
                     mask_interpolation_method='Linear',
                     mask_interpolation_threshold=0.5,
                     list_of_patient_folders=['1'],
                     nifti_image='phantom.nii.gz',
                     number_of_threads=1)
prep.resample()
```

### IBSI I Config. B (DICOM):
In this example, we perform resampling on the DICOM phantom studied in IBSI I Configuration B.

* Studied structure: GTV-1;
* Slice-wise resampling (2D);
* Linear interpolation 2mm × 2mm (axial);
* Linear ROI interpolation;
* ROI rounding threshold 0.5.

```python
prep = Preprocessing(load_dir='Test_Cases/IBSI I/DICOM', 
                     save_dir='Test_Cases/IBSI I/Save/B_DICOM',
                     input_data_type='DICOM', 
                     input_imaging_mod='CT', 
                     structure_set=['GTV-1'], 
                     just_save_as_nifti=False, 
                     resample_resolution=2.0, 
                     resample_dimension='2D',
                     image_interpolation_method='Linear',
                     mask_interpolation_method='Linear',
                     mask_interpolation_threshold=0.5,
                     list_of_patient_folders=['1'],
                     number_of_threads=1)
prep.resample()
```

### IBSI I Config. C and Config. D (DICOM):
In this example, we perform resampling on the DICOM phantom studied in IBSI I. Resampling for Configurations C and D are identical.

* Studied structure: GTV-1;
* Single volume (3D) resampling;
* Linear interpolation 2mm × 2mm × 2mm;
* Linear ROI interpolation;
* ROI rounding threshold 0.5.

```python
prep = Preprocessing(load_dir='Test_Cases/IBSI I/DICOM', 
                     save_dir='Test_Cases/IBSI I/Save/C_D_DICOM',
                     input_data_type='DICOM', 
                     input_imaging_mod='CT',
                     structure_set=['GTV-1'], 
                     just_save_as_nifti=False, 
                     resample_resolution=2.0, 
                     resample_dimension='3D',
                     image_interpolation_method='Linear', 
                     mask_interpolation_method='Linear', 
                     mask_interpolation_threshold=0.5, 
                     list_of_patient_folders=['1'],  
                     number_of_threads=1)
prep.resample()
```

### IBSI I Config. E (NIFTI):
In this example, we perform resampling on the NIFTI phantom studied in IBSI I Configuration E.

* Studied structure: mask;
* NIfTI image: phantom.nii.gz;
* Single volume (3D) resampling;
* BSpline interpolation 2mm × 2mm × 2mm;
* Linear ROI interpolation;
* ROI rounding threshold 0.5.

```python
prep = Preprocessing(load_dir='Test_Cases/IBSI I/NIFTI', 
                     save_dir='Test_Cases/IBSI I/Save/E_NIFTI',
                     input_data_type='NIFTI', 
                     input_imaging_mod='CT',  
                     structure_set=['mask'], 
                     just_save_as_nifti=False,
                     resample_resolution=2.0, 
                     resample_dimension='3D',
                     image_interpolation_method='BSpline', 
                     mask_interpolation_method='Linear',
                     mask_interpolation_threshold=0.5, 
                     list_of_patient_folders=['1'], 
                     nifti_image='phantom.nii.gz',
                     number_of_threads=1)
prep.resample()
```

### IBSI II Ph. II Config. B (NIFTI):
In this example, we perform resampling on the NIFTI phantom studied in IBSI II Phase II Configuration B.

* Studied structure: mask;
* NIfTI image: phantom.nii.gz;
* Single volume (3D) resampling;
* BSpline interpolation 1mm × 1mm × 1mm;
* Linear ROI interpolation;
* ROI rounding threshold 0.5.

```python
prep = Preprocessing(load_dir='Test_Cases/IBSI II/NIFTI', 
                     save_dir='Test_Cases/IBSI II/NIFTI',
                     input_data_type='NIFTI', 
                     input_imaging_mod='CT', 
                     structure_set=['mask'],
                     just_save_as_nifti=False, 
                     resample_resolution=1.0, 
                     resample_dimension='3D',  
                     image_interpolation_method='BSpline',
                     mask_interpolation_method='Linear', 
                     mask_interpolation_threshold=0.5,
                     list_of_patient_folders=['1'],
                     nifti_image='phantom.nii.gz',
                     number_of_threads=1)
prep.resample()
```
