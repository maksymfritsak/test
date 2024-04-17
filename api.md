# Prerequisites
To install the most recent version of rad:

```python
pip install ...
```

# Preprocessing:

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

> class Preprocessing(load_dir, save_dir, input_data_type, input_imaging_mod, structure_set=None,
                 just_save_as_nifti=False, resample_resolution=1.0, resample_dimension='3D',
                 image_interpolation_method='Linear',
                 mask_interpolation_method='Linear', mask_interpolation_threshold=.5,
                 start_folder=None, stop_folder=None, list_of_patient_folders=None,
                 nifti_image=None,number_of_threads=1)

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

7) structure_set: {None, ['ExtractAllMasks']}

   Data Type: Either `None` or a list containing elements of type `str`.

   Default: None

  This parameter takes a list of structure names one wants to resample, for example ['lung', 'liver', 'CTV_1'].

  There are some conventional values for this parameter:

  None - no structures are taken into account and only the image is resampled;

  ['ExtractAllMasks'] - only for DICOM, takes all structures in the RTstruct file.

8) just_save_as_nifti: {True, False}

   Data Type: bool

   Default: Flase

   Only for DICOM, if True saves the image and specified structures as NIfTI files without resampling.

9) resample_resolution

   Data Type: float

   Default: 1.0

   Resolution to which image will be resampled (in mm).

10) resample_dimension: {'2D', '3D'}

    Data Type: str

    Default: '3D'

    '3D': the image is resampled isotropicaly.
    '2D': image is resampled inplane while original spacing is jeeped in the z-direction.
    

   

  

  

  
   


```
This is some text in a box!
```

