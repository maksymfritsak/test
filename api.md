---
layout: default
theme: architect
---

# Prerequisites
To install the most recent version of rad:

```python
pip install ...
```
This approach is dedicated to users who are fluent in programming with Python and provides a great opportunity to integrate RAD into the research workflow without the necessity of interaction with the User Interface.

* [Resampling](api_prep.md);
* Filtering;
* Radiomics.


# Radiomics:

> class Radiomics:(load_dir, save_dir, input_data_type, input_imaging_mod, structure_set,
                 aggr_dim, aggr_method, intensity_range=None, outlier_range=None,
                 number_of_bins=None, bin_size=None, slice_weighting=False, slice_median=False,
                 start_folder=None, stop_folder=None, list_of_patient_folders=None,
                 nifti_image=None, number_of_threads=1):

1) load_dir

   dtype: str
   

   Path to the load directory where patient folders are located.

3) save_dir

   dtype: str

   Path to the directory where data will be saved. If the directory does not exist, rad will create it.

4) input_data_type: {'DICOM', 'NIFTI'}

   dtype: str

   Rad supports both Dicom and NIfTI standards, consult GetStarted for the further details on how both data types are handled.

5) input_imaging_mod: {'CT', 'PT', 'MR'}

   dtype: str

   The modality of your images, modalities should be the same among all you patients. How rad handles modalities read at the Get started.

7) structure_set: {['ExtractAllMasks']}

   Data Type: List containing elements of type `str`.

   This parameter takes a list of structure names one wants to resample, for example ['lung', 'liver', 'CTV_1'].

   There are some conventional values for this parameter:
   
   ['ExtractAllMasks'] - only for DICOM, takes all structures in the RTstruct file.

9) aggr_dim: {'2D', '2.5D', '3D'}

   Data Type: str

   Default: '3D'

10) aggr_method: {'MERG', 'AVER', 'SLICE_MERG', 'DIR_MERG'}

    Data Type: str

    Default: 'AVER'

11) intensity_range:
    Data Type: List of elements type float/int or None

    Default: None

    If not None then voxels with intensities outside from the provided intensity_range are excluded from the intensity ROI mask. Example intensity_range = [-1000, 500].
    
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
    
18) start_folder, stop_folder

    Data Type: None or int

    Default: None
  
    If both start_folder and stop_folder are not None, then rad will take all patient folders in the range [start_folder, stop_folder]. For this to work ALL folders in the load_dir should contain ONLY int in their names.

    list_of_patient_folders

    Data Type: None or list of elements of type 'str'

    Default: None

    If list_of_patient_folders is not None, then rad will take all folders from the defined list. Note, in this case folders can contain any sybols or letters in their names.

    If all start_folder, stop_folder, and list_of_patient_folders are None then rad will take all folders from the load_dir. Note, in this case, folders can contain any symbols or letters in their names.

19) nifti_image

    Data Type: None or str

    Default: None

    Only for input_data_type = 'NIFTI', specify the name of the NIfTI image file, e.g. nifti_image = 'image.nii.gz'.

    Important to provide the file name with the file extension (both .nii and .nii.gz are supported). NIfTI image files should have IDENTICAL names for ALL the patients in the study.

20) number_of_threads

    Data Type: int

    Default: 1

    If greater than 1 - performs multiprocessing and distributes tasks among cores. Each core takes one patient. Mind the RAM when chousing the big amount of threads.


# Methods:

resample(): performs resampling


# Examples:


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

