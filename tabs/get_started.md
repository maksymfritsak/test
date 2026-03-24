## Installation

### Option 1: Windows executable file
The simplest way to run Z-Rad on Windows is to start the `z-rad.exe` attached to every Z-Rad release.

### Option 2: Install from GitHub (Windows, Linux, macOS)
Use this option if you want to run Z-Rad from source code.

* Clone the repository:
   
```sh
git clone https://github.com/medical-physics-usz/z-rad.git
cd z-rad
```

* (Optional but recommended) Create and activate a virtual environment.

* Install dependencies:

```sh
pip install -r requirements.txt
```

* Run the `main.py` file:

```sh
python main.py
```

## Support 
 * Windows, macOS, Linux
 * DICOM, NIfTI
 * CT, MRI, PET, Mammography, 3D Dose Distribution
   
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
      │    ├── folder_1/
      │    ├── folder_2/
      │    ├── ...
      │    └── folder_n/
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
Each <code>folder_i</code> must contain exactly one imaging series (e.g., PET, CT, MRI, mammography, or 3D dose distribution) and no more than one RTSTRUCT file. If multiple RTSTRUCT files are present, only the first detected file will be used.
</p>

<p>
<b>NIfTI data:</b><br>
Each <code>folder_i</code> may contain multiple imaging modalities along with their corresponding segmentation masks, stored as <code>.nii</code> or <code>.nii.gz</code> files. To ensure consistent processing across folders, image files that are intended to be processed together must have identical filenames in all folders.
</p>

</div>
