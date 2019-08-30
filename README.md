# **Finding Lane Lines on the Road using Python and OpenCV** 

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project we will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.

Results
---
Testing versus two video streams captured from real car (full videos can be found under test_video/ and test_video_output/)

![GIF File](test_videos_output/solidWhiteRight.gif)

Code
---
In  order to reach this result I have defined a stream pipeline as follow 

1. Load test images
2. Apply grayscale transform
3. Smooth the image to suppress noise and any spurious gradients
4. Apply Canny edge detection algorithm
5. Cut-out any edges that are out of the lane lines region (**region of interest**)
6. Get the lines located in the region of interest using hough transform
7. Fitting and extrapolating these lines for both right and left lane
   * Determining the x and y points of each of the right and left lane lines
   * Extrapolating or fitting these points for both lane lines
8. Draw the lane lines on the original image
   * Drawing the lane lines on a blank image firstly
   * Weighting the original image with the lane lines image

Note : The defined pipeline uses 1-D polyfit so it can detect straight lines only, lanes curvature are beyond scope of this project.
