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

    '3D': the image is resampled isotropically.
    '2D': image is resampled in-plane while original spacing is jeeped in the z-direction.
    
11) image_interpolation_method: {'NN', 'Linear', 'BSpline', 'Gaussian'}

    Data Type: str

    Default: 'Linear'


12) mask_interpolation_method: {'NN', 'Linear', 'BSpline', 'Gaussian'}

    Data Type: str

    Default: 'Linear'

13) mask_interpolation_threshold:

    Data Type: float in the range [0, 1]

    Default: 0.5
    
14) start_folder, stop_folder

    Data Type: None or int

    Default: None
  
    If both start_folder and stop_folder are not None, then rad will take all patient folders in the range [start_folder, stop_folder]. For this to work ALL folders in the load_dir should contain ONLY int in their names.

    list_of_patient_folders

    Data Type: None or list of elements of type 'str'

    Default: None

    If list_of_patient_folders is not None, then rad will take all folders from the defined list. Note, in this case folders can contain any sybols or letters in their names.

    If all start_folder, stop_folder, and list_of_patient_folders are None then rad will take all folders from the load_dir. Note, in this case folders can contain any sybols or letters in their names.

15) nifti_image

    Data Type: None or str

    Default: None

    Only for input_data_type = 'NIFTI', then specify the name of the nifti image file, e.g. nifti_image = 'image.nii.gz'.

    Important to provide the file extension (both .nii and .nii.gz are supported). NIfTI image files should have IDENTICAL names for the patients you study.

16) number_of_threads

    Data Type: int

    Default: 1

    If greater than 1 - performs multiprocessing and distributes tasks among cores. Each core takes one patient. Mind the RAM when chousing the big amount of threads.


# Methods:

resample(): performs resampling


# Examples:
