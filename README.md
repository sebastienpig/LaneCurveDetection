# LaneCurveDetection

## This project aims at detecting lanes on a road and its curvature

Visual includes coloring the surface between the left and the right lanes

Pipeline includes:

1. acquiring image

2. filtering the image

3. undistorting the image

4. choosing a region of interest to warp/unwarp

5. warp the region of interest

6. get an histogram and detect left and right lane from histogram

7. fit a polynom from the detected lanes

8. color the area between the lanes

9. add to the original image and unwarp the combined image

10. calculate the curvature

11. process the video stream

