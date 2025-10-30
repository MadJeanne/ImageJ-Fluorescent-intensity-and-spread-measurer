# kymograph and concentric rings analysis - ImageJ-Fluorescent-intensity-and-spread-measurer
This repository provides macros, scripts, and workflow documentation for analyzing fluorescence signal dynamics using kymographs and heatmaps, as well as validating and visualizing responses through concentric ring analysis.
heatmap validation workflow
step 1: run validation macro

Run the macro 250904R_Macro_HeatMap_0v0.ijm located in the Macro folder on all videos of interest.
This step determines which videos are usable based on the following criteria:
the origin of the response and peak intensity are within the field of view,
most of the response spreads across the imaged area.

step 2: select valid slices

Decide which slices to retain based on the above criteria.
You can note how many slices per day or per condition are analyzed for consistency.

Generating heatmap montages

Open all validated heatmaps.

Convert them into a single stack:
Image → Stacks → Images to Stack

Create a montage:
Image → Stacks → Make Montage

On the montage, select a threshold that works well across all images.
Record this threshold value.
Update it in the macro 250824U_Macro_dLight_diffusion_0v8.ijm
(variable thresh, line 49).

generating kymograph montages

Open the kymographs for each group separately:
ex:
F WT
F GKI Het
M WT
M GKI Het

Convert images to stacks:
Image → Stacks → Images to Stack
Use Center method if alignment is required.
Give clear names and sort by titles containing experimental conditions (e.g.: “IFN” or “CTRL”).
Save each stack as a .tif file.

Open the stacks and generate montages:
Image → Stacks → Make Montage
Save each montage as .tif.

For consistent brightness across montages:
Open Adjust → Threshold / Brightness & Contrast.
Identify the image with the lowest maximum intensity.
Apply this max value to all other montages using the Set button in the Brightness/Contrast manager.

determining a global threshold:
To choose an appropriate threshold value across all images:
Open all maximum projections obtained from the heatmap validation step.
Run Image → Stacks → Make Montage.
Visually determine a threshold that best balances contrast and background noise across all datasets

exporting logs to excel
Log files are automatically saved as .txt.
To import them into Excel:
Open Excel.
Use “Open” or drag the .txt file in.
Save the file as an Excel Workbook (.xlsx) using F12 or Save As.
