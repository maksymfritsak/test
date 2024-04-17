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

| Parameters |Center Align |
|:-----------|:------------|
| load_dir   |dtype: str   |


```
This is some text in a box!
```

