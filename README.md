# Self-Driving Car Component

This project implements a computer vision module for a self-driving car system using OpenCV and Python. It is designed to detect road features (such as lane markings) from a video feed and calculate the vehicle's lateral distance from these features.

## Project Overview

The system processes video input to identify vertical edges, which typically correspond to lane lines on a road. By analyzing these features, the script computes the distance between the center of the vehicle (frame center) and the detected lane markings, providing essential data for steering control.

![Project Screenshot](img/Screenshot%202025-12-02%20005517.png)

## Key Features

*   **Vertical Edge Detection:** Utilizes a custom convolution kernel to highlight vertical edges in the video frames.
*   **Image Processing Pipeline:**
    *   Grayscale conversion
    *   2D Filtering (Convolution)
    *   Thresholding to binary image
    *   Morphological Opening to remove noise
*   **Region of Interest (ROI):** Focuses processing on the lower part of the frame (road surface) by masking the top section.
*   **Contour Detection & Tracking:** Finds contours of significant area to identify road markings.
*   **Distance Estimation:** Calculates the horizontal offset (distance) between the frame's center and the centroid of the detected object.
*   **Visual Feedback:** Draws rotated bounding boxes around detected features and overlays the calculated distance on the video feed.

## Technologies Used

*   **Python**
*   **OpenCV (cv2)**
*   **NumPy**

## How it Works

1.  **Input:** Reads video frames from `Samples/road_drive.avi`.
2.  **Preprocessing:** The frame is converted to grayscale and convolved with a vertical edge detection kernel.
3.  **Feature Extraction:** Thresholding and morphological operations isolate the lane markings.
4.  **Analysis:** The script finds contours, filters them by size, and calculates their centroids.
5.  **Output:** The original frame is annotated with bounding boxes and distance measurements, and displayed alongside intermediate processing stages.
