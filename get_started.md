## Supported Platforms: Windows, macOS, Linux

## Data Structure
To run Z-Rad on your data, it must be organized in a specific directory structure. To process `folder_1`, `folder_2`, …, `folder_n`, the data should be arranged as follows:
```
main_path/
└── data_folder/
    ├── folder_1/
    ├── folder_2/
    ├── ...
    └── folder_n/
```
<div style="text-align: justify;">

The `data_folder` refers to the project directory, while `folder_1`, `folder_2`, …, `folder_n` denote the individual folders containing the imaging data to be processed.

For projects involving multiple imaging modalities or data types, it is recommended to organize the data using a consistent folder structure, as illustrated below for PET/CT studies:

</div>
```
main_path/
├── PET/
│   ├── folder_1/
│   ├── folder_2/
│   ├── ...
│   └── folder_n/
└── CT/
    ├── folder_1/
    ├── folder_2/
    ├── folder_2/
    ├── ...
    └── folder_n/
```


<div style="text-align: justify;">

<p>
Z-Rad supports both DICOM and NIfTI file formats for the folder content.
</p>

<p>
<b>DICOM data:</b><br>
Each `folder_i` must contain exactly one imaging series (e.g., PET, CT, MRI, mammography, or 3D dose distribution) and no more than one RTSTRUCT file. If multiple RTSTRUCT files are present, only the first detected file will be used.
</p>

<p>
<b>NIfTI data:</b><br>
Each `folder_i` may contain multiple imaging modalities along with their corresponding segmentation masks, stored as `.nii` or `.nii.gz` files. To ensure consistent processing across folders, image files that are intended to be processed together must have identical filenames in all folders.
</p>

</div>
