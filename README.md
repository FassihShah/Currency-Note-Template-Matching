# Currency Note Template Matching using OpenCV

## Overview
This project implements a computer vision solution to detect and locate the face of Quaid-e-Azam on Pakistani currency notes using **template matching** with OpenCV. Along with the face detection, the program identifies and marks two identification number regions on the note based on relative offsets from the detected face.

---

## Features

- **Template Matching with Rotation and Scaling:**  
  Robust detection using multi-scale and multi-angle template matching for notes photographed under varying zoom levels and orientations.

- **Preprocessing:**  
  Grayscale conversion, histogram equalization, and Gaussian blur for improved matching accuracy.

- **Dynamic Bounding Boxes:**  
  Bounding boxes for Quaid-e-Azam’s face and two identification number regions dynamically scaled and positioned relative to the matched template size.

- **Output:**  
  Annotated images saved to an output folder and identification number coordinates exported to a CSV file.

---

## Methodology

1. **Preprocessing**  
   - Convert images to grayscale.  
   - Apply histogram equalization (`cv2.equalizeHist`) to improve contrast.  
   - Use Gaussian Blur to reduce noise while preserving key features.

2. **Template Matching**  
   - Use `cv2.matchTemplate` with `cv2.TM_CCOEFF_NORMED` similarity metric.  
   - Perform matching over multiple scales (`0.9x`, `1.0x`, `1.1x`) and rotations (`-90°` to `+90°`) for rotation and scale invariance.  
   - Select the best matching location with the highest similarity score above a threshold.

3. **Bounding Boxes**  
   - Draw a green rectangle around the matched face.  
   - Draw two blue rectangles around the top-right and bottom-left identification numbers based on relative offsets and sizes scaled by the template dimensions.  
   - Adjust bounding boxes using a custom function to prevent overflow outside the image boundaries.

4. **Output**  
   - Save annotated images in the output directory.  
   - Save detected identification box coordinates to a CSV file for further analysis.

---
