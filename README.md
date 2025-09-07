# LV-segmentation-MRI

![Deep Learning result sample](demo/DL_demo.jpg)

## Overview

This project addresses the **Automatic Cardiac Diagnostic Challenge (ACDC)**, focusing on **left ventricle (LV) segmentation** in MRI images. The tool integrates two fully automatic segmentation methods: **K-means clustering** and **deep learning (Mask R-CNN)**, unified in a **Python + MATLAB GUI** for ease of use.

Key features:
- Automatic segmentation of the **left ventricle endocardium** during **diastole** and **systole**.
- Calculation of **ventricle cavity volumes** (End-Diastolic, End-Systolic) and **Ejection Fraction**.
- GUI interface allowing users to switch between segmentation methods and visualize results.
- Deep learning pipeline built on **TensorFlow**, with dataset creation, training, and validation integrated into the GUI.
- Tested on a database of **100 patients**, achieving significant precision for both methods.

---

## Folder Structure
```
├── EvaluationImages/ # Sample MRI images for evaluation
├── icons/ # GUI icons
├── Left-Ventricle-Database/ # Training dataset for Mask R-CNN
│ ├── annots/
│ ├── images/
│ └── masks/
├── SegmentedImages/ # Segmentation results
├── demo/ # Demo videos and images
├── LV_Segmentation.exe # Windows executable for GUI tool
├── Mask_RCNN_segmentation.py # Deep Learning segmentation script
├── network_training_LV.py # Mask R-CNN training script
└── mccExcludedFiles.log
```
---

## Installation

1. Install **Python 3.7** and required packages:

```bash
pip install numpy matplotlib tensorflow opencv-python
```
2. Install MATLAB 2019 for GUI integration. Ensure MATLAB path is set correctly.

3. (Optional) For Mask R-CNN training:
```bash
pip install torch torchvision
```
## Usage

1. Launch LV_Segmentation.exe (Windows) or run MATLAB GUI.

2. Select Segmentation Method: K-means or Deep Learning.

3. Load Patient Data: Load MRI images in NIFTI format.

4. Create ROI (for Deep Learning): Generate masks (Ellipse, Polygon, Free-Hand) to prepare the training dataset.

5. Run Segmentation:

  - Process single image or full patient folder.

  - Segmented images saved in SegmentedImages/.

  - Metrics (EDV, ESV, EF) displayed in GUI.

6. Visualize Results:

  - Systole and diastole phases can be navigated.

  - Demo videos in demo/ folder illustrate segmentation outcomes
