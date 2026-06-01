# White Blood Cell Segmentation in B-ALL Microscopy Images
## Project overview

This project focuses on the segmentation of dark purple-stained lymphoblast nuclei in microscopy images from patients diagnosed with B-lineage Acute Lymphoblastic Leukemia (B-ALL).

The aim of the project is to compare manually created segmentation masks with automatically generated masks using a classical, non-AI image processing approach.

Manual masks were created in Fiji/ImageJ and used as ground truth. Automatic masks were generated in Python using color-based thresholding, Otsu-based background exclusion, morphological post-processing, and connected component filtering.

## Dataset

The dataset used in this project is the ALL subset of the SN-AM dataset from The Cancer Imaging Archive (TCIA).

- Dataset: SN-AM Dataset
- Subset used: ALL images
- Imaging modality: light microscopy
- Image format: BMP
- Number of selected images: 10
- Structure of interest: dark purple-stained lymphoblast nuclei
- License: CC BY 3.0

The full dataset can be accessed here:  
https://doi.org/10.7937/tcia.2019.of2w8lxr

Only the selected images used in this project are included in the repository.

## Repository structure

```text
.
├── appendix/
│   ├── appendix1.png
│   ├── appendix2.png
│   ├── appendix3.png
│   └── appendix4.png
├── notebook/
│   └── Project_work_CO4_SERNA_SUERER.ipynb
├── presentation/
│   └── presentation file
├── results/
│   ├── evaluation_dice_scores.csv
│   └── feature_extraction_results.csv
├── README.md
├── LICENSE
└── .gitignore
```
## Methods

The project contains a complete mini segmentation workflow:

- manual segmentation in Fiji/ImageJ
- automatic segmentation in Python
- Dice score evaluation
- simple feature extraction from manual and automatic masks

The automatic segmentation uses a classical image processing approach with Gaussian smoothing, RGB channel-based thresholding, Otsu-based background exclusion, morphological operations, and connected component filtering.

## Results

The automatic masks were compared with the manual ground truth masks using the Dice similarity coefficient.

**Mean Dice score:** `0.581 ± 0.175`

This shows a moderate agreement between manual and automatic segmentation. The method worked best for clearly stained and well-separated nuclei, but was less reliable in images with weak contrast, overlapping structures, or many red blood cell edges.

## Feature extraction

For each image, the number of segmented nuclei and the total segmented area were extracted from both manual and automatic masks.

The comparison showed that automatic segmentation sometimes overestimated the number of nuclei and segmented area because red blood cell edges and background artifacts were falsely detected.

## Visual examples

### Segmentation overview

![Segmentation overview](appendix/appendix2.png)

### Nuclei count comparison

![Nuclei count comparison](appendix/appendix3.png)

### Segmented area comparison

![Segmented area comparison](appendix/appendix4.png)

## Result files

The numerical results are stored in the `results/` folder:

- `evaluation_dice_scores.csv`
- `feature_extraction_results.csv`

## How to run

Open the notebook in Jupyter or VS Code and run all cells:

```text
notebook/Project_work_CO4_SERNA_SUERER.ipynb
