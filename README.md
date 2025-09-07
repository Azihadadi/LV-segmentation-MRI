# LV-segmentation-MRI

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

1. Launch the GUI:
   - On Windows: run `LV_Segmentation.exe`
   - On MATLAB: open the GUI script.
2. Select the **Segmentation Method**: K-means or Deep Learning.
3. **Load Patient Data**:
   - Select MRI images in NIFTI format for processing.
4. **Create ROI (for Deep Learning)**:
   - Generate masks using Ellipse, Polygon, or Free-Hand tools.
   - Masks are stored in `Left-Ventricle-Database/masks/` and annotations in `Left-Ventricle-Database/annots/`.
5. **Run Segmentation**:
   - Process a single image or full patient folder.
   - Segmented images saved in `SegmentedImages/`.
   - Calculated metrics (EDV, ESV, EF) are displayed in the GUI.
6. **Visualize Results**:
   - Navigate through systole and diastole phase images.
   - Demo videos in the `demo/` folder show full workflow examples.

---

## Deep Learning Pipeline

The deep learning workflow consists of three main stages:

1. **Dataset Creation**:
   - Convert NIFTI files to JPG images.
   - Generate masks for each image to prepare the training set.
2. **Training**:
   - Train the Mask R-CNN model using the created dataset.
   - Multiple epochs supported; training weights saved after each epoch.
3. **Validation**:
   - Segment unseen images or full patient folders.
   - Outputs include segmented masks and calculated cardiac metrics.
   - Progress bar displayed in GUI; validation results can be exported.

---

## Demo

Demo content located in `demo/` folder:
- Example image: `DL_demo.jpg`
- Demo videos: `demo_run1.mp4`, `demo_run2.mp4`
  
<img src="demo/DL_demo.jpg" alt="Deep Learning result sample" width="400"/>


---

## References

- [ACDC Challenge](http://acdc.creatis.insa-lyon.fr/)
- [MICCAI Emidec Challenge 2020](http://stacom2020.cardiacatlas.org/accepted-papers/)
- [Matterport Mask R-CNN](https://github.com/matterport/Mask_RCNN)

---

## Notes

- Developed as part of a **Master's thesis** in collaboration with **CHU Dijon Hospital**.
- Dataset includes **registered cine- and delayed-enhancement MRI scans**.
- Designed as a research-focused tool suitable for **further development and industrial evaluation**.

---


