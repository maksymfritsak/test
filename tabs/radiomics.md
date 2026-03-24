# Z-Rad: Radiomics Extraction

![Radiomics Tab](../figures/Rad_tab.png "Radiomics Tab")

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

</div>

<p><b>GUI Available Radiomic Features:</b></p>

<div style="overflow-x: auto; overflow-y: auto; max-height: 400px;">

<table border="1" cellpadding="6" cellspacing="0" style="border-collapse: collapse; width: 100%; text-align: left;">

<tr>
<th style="position: sticky; top: 0; background: white;">Morphological features</th>
<th style="position: sticky; top: 0; background: white;">Local intensity features</th>
<th style="position: sticky; top: 0; background: white;">Intensity-based statistical features</th>
<th style="position: sticky; top: 0; background: white;">Intensity histogram features</th>
<th style="position: sticky; top: 0; background: white;">GLCM features</th>
<th style="position: sticky; top: 0; background: white;">GLRLM features</th>
<th style="position: sticky; top: 0; background: white;">GLSZM / GLDZM features</th>
</tr>

<tr><td>Volume (mesh)</td><td>Local intensity peak</td><td>Mean</td><td>Mean</td><td>Joint maximum</td><td>Short runs emphasis</td><td>Small zone / distance emphasis</td></tr>
<tr><td>Volume (voxel counting)</td><td>Global intensity peak</td><td>Variance</td><td>Variance</td><td>Joint average</td><td>Long runs emphasis</td><td>Large zone / distance emphasis</td></tr>
<tr><td>Surface area (mesh)</td><td></td><td>Skewness</td><td>Skewness</td><td>Joint variance</td><td>Low grey level run emphasis</td><td>Low grey level emphasis</td></tr>
<tr><td>Surface to volume ratio</td><td></td><td>(Excess) kurtosis</td><td>(Excess) kurtosis</td><td>Joint entropy</td><td>High grey level run emphasis</td><td>High grey level emphasis</td></tr>
<tr><td>Compactness 1</td><td></td><td>Median</td><td>Median</td><td>Difference average</td><td>Short run low grey level emphasis</td><td>Small zone low grey level emphasis</td></tr>
<tr><td>Compactness 2</td><td></td><td>Minimum</td><td>Minimum</td><td>Difference variance</td><td>Short run high grey level emphasis</td><td>Small zone high grey level emphasis</td></tr>
<tr><td>Spherical disproportion</td><td></td><td>10th percentile</td><td>10th percentile</td><td>Difference entropy</td><td>Long run low grey level emphasis</td><td>Large zone low grey level emphasis</td></tr>
<tr><td>Sphericity</td><td></td><td>90th percentile</td><td>90th percentile</td><td>Sum average</td><td>Long run high grey level emphasis</td><td>Large zone high grey level emphasis</td></tr>
<tr><td>Asphericity</td><td></td><td>Maximum</td><td>Maximum</td><td>Sum variance</td><td>Grey level non-uniformity</td><td>Grey level non-uniformity</td></tr>
<tr><td>Centre of mass shift</td><td></td><td>Interquartile range</td><td>Mode</td><td>Sum entropy</td><td>Normalised grey level non-uniformity</td><td>Normalised grey level non-uniformity</td></tr>
<tr><td>Maximum 3D diameter</td><td></td><td>Range</td><td>Interquartile range</td><td>Angular second moment</td><td>Run length non-uniformity</td><td>Zone size / distance non-uniformity</td></tr>
<tr><td>Major axis length</td><td></td><td>Mean absolute deviation</td><td>Range</td><td>Contrast</td><td>Normalised run length non-uniformity</td><td>Normalised zone size / distance non-uniformity</td></tr>
<tr><td>Minor axis length</td><td></td><td>Robust mean absolute deviation</td><td>Mean absolute deviation</td><td>Dissimilarity</td><td>Run percentage</td><td>Zone percentage</td></tr>
<tr><td>Least axis length</td><td></td><td>Median absolute deviation</td><td>Robust mean absolute deviation</td><td>Inverse difference</td><td>Grey level variance</td><td>Grey level variance</td></tr>
<tr><td>Elongation</td><td></td><td>Coefficient of variation</td><td>Median absolute deviation</td><td>Normalised inverse difference</td><td>Run length variance</td><td>Zone size / distance variance</td></tr>
<tr><td>Flatness</td><td></td><td>Quartile coefficient of dispersion</td><td>Coefficient of variation</td><td>Inverse difference moment</td><td>Run entropy</td><td>Zone size / distance entropy</td></tr>
<tr><td>Volume density (AABB)</td><td></td><td>Energy</td><td>Quartile coefficient of dispersion</td><td>Normalised inverse difference moment</td><td></td><td></td></tr>
<tr><td>Area density (AABB)</td><td></td><td>Root mean square</td><td>Entropy</td><td>Inverse variance</td><td></td><td></td></tr>
<tr><td>Volume density (AEE)</td><td></td><td>Uniformity</td><td></td><td>Correlation</td><td></td><td></td></tr>
<tr><td>Area density (AEE)</td><td></td><td>Maximum histogram gradient</td><td></td><td>Autocorrelation</td><td></td><td></td></tr>
<tr><td>Volume density (MVEE)</td><td></td><td>Maximum histogram gradient intensity</td><td></td><td>Cluster tendency</td><td></td><td></td></tr>
<tr><td>Area density (MVEE)</td><td></td><td>Minimum histogram gradient</td><td></td><td>Cluster shade</td><td></td><td></td></tr>
<tr><td>Volume density (convex hull)</td><td></td><td>Minimum histogram gradient intensity</td><td></td><td>Cluster prominence</td><td></td><td></td></tr>
<tr><td>Area density (convex hull)</td><td></td><td>Integrated intensity</td><td></td><td>Information correlation 1</td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>Information correlation 2</td><td></td><td></td></tr>

</table>

</div>

<div style="text-align: justify;">
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
