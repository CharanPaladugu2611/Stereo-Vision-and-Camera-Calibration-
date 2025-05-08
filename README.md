# 📸 Stereo Vision and Camera Calibration 
This project implements a full stereo vision pipeline using OpenCV — starting from camera calibration using a checkerboard video, and advancing through stereo matching, rectification, disparity map generation, depth estimation, and epipolar geometry visualization.

The pipeline is split into two major parts:

1. Monocular Camera Calibration using a Chessboard Video

2. Stereo Vision System on test datasets (classroom, traproom, storageroom)

It is built to be modular, interpretable, and visually demonstrative — ideal for understanding every step in a stereo vision pipeline.

## 🧰 Technologies Used
* Python 3.x

* OpenCV (SIFT, StereoSGBM, calibration modules)

* NumPy, Matplotlib

* Google Colab + Drive (for input/output)

## 🧱 Project Highlights
✅ Part 1: Camera Calibration (Monocular)
* Extracts frames from a chessboard video using Laplacian variance to filter sharp images

* Detects 9×6 inner corners using ```cv2.findChessboardCorners```

* Computes intrinsic matrix and distortion coefficients with ```cv2.calibrateCamera```

- Undistorts each image using ```cv2.undistort``` + ```cv2.getOptimalNewCameraMatrix```

* Compares original vs undistorted images with corner overlays

* Computes reprojection error and visualizes it

* Projects 3D points to 2D and compares detected corners to reprojected ones

✅ Part 2: Stereo Vision Pipeline
* Loads stereo images (im0.png, im1.png) and calibration data from .txt files

* Detects features using SIFT + FLANN matcher

* Estimates Fundamental Matrix using RANSAC

* Computes and decomposes the Essential Matrix

* Applies stereoRectifyUncalibrated to align views

* Computes Disparity Map using StereoSGBM

* Generates Depth Map from disparity using focal length and baseline

* Overlays Epipolar Lines on rectified images for validation

## 🔍 Sample Outputs
📷 Undistorted vs Distorted Chessboard Corners
Yellow = original corners
Pink = undistorted corners (on original image)
![image](https://github.com/user-attachments/assets/939f55d1-106c-4b80-8718-5b00972af4ed)

📊 Reprojection Error Plot
Displays pixel-level error per calibration frame
![image](https://github.com/user-attachments/assets/3802cae7-8c9a-4864-a743-fe7fde77f25f)

