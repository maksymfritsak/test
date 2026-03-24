# Z-Rad: Radiomics Extraction

![Radiomics Tab](Rad_tab.png "Radiomics Tab")

<div style="text-align: justify;">

<p>
The upper part <b>(1)</b> of the Radiomics tab is identical in layout to the corresponding section in the Preprocessing and Filtering tabs.
</p>

<p>
Under Data Type <b>(2)</b>, the user can select whether the input images are provided in DICOM or NIfTI formats.
</p>

<p>
The Intensity Range <b>(3)</b> option enables restriction of the analyzed voxel intensities to a user-defined range. This is useful for excluding irrelevant intensity values and ensuring that radiomic features are computed only within the desired signal interval.
</p>

<p>
The Outlier Removal (in σ) <b>(4)</b> option enables removal of extreme voxel values based on a specified number of standard deviations. This excludes high or low intensity voxels, however may produce “holes” in the segmentation mask.
</p>

<p>
The Texture Aggregation Method <b>(5)</b> defines how texture matrices are combined during radiomic feature calculation. The available aggregation strategies include <b>2D</b> (slice-wise), <b>2.5D</b> (aggregation across directions or slices), and full <b>3D</b> aggregation. Since texture features may vary depending on the aggregation strategy, this parameter should be selected consistently across all analyzed cases.
</p>

<p>
The Discretization <b>(6)</b> setting specifies how image intensities are discretized prior to texture feature computation. Two IBSI-compliant strategies are supported: <b>fixed bin size (FBS)</b>, where a constant intensity width is used for binning, and <b>fixed bin number (FBN)</b>, where the number of gray levels is predefined. The choice of discretization strategy and its parameters (bin size or number of bins) strongly influences higher-order texture features.
</p>

<p>
After all parameters have been configured, pressing RUN <b>(7)</b> initiates the radiomics extraction pipeline. The resulting feature tables are saved in the selected output directory as <code>.csv</code> files. Each file begins with the patient ID, followed by the mask ID, bounding box dimensions, number of voxels within the mask, and the number of bins used for discretization. These are followed by the extracted radiomic features. All radiomic features and aggregation methods are computed in accordance with IBSI I.
</p>

<p><b>Note:</b></p>

<ul>
<li>
Intensity–volume histogram features, as well as computationally expensive features such as Moran’s I and Geary’s C, are not available in the GUI and can only be accessed through the API.
</li>
</ul>

<p><b>Note:</b></p>

<ul>
<li>
<b>Save Input:</b> Save your configuration by going to the File menu and clicking Save Input, or using the shortcut <code>Ctrl+S</code>.
</li>
<li>
<b>Load Input:</b> Load a previously saved configuration by navigating to the File menu and selecting Load Input or pressing <code>Ctrl+O</code>.
</li>
</ul>
</div>
