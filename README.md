# LaneCurveDetection

## This project aims at detecting lanes on a road and its curvature

Visual includes coloring the surface between the left and the right lanes

Pipeline includes:



<h3> Undistorting the image </h3>

The calibration of the camera is done through a chessboard view under different angles.
Parameters are saved and used later on.

The openCV function used is cv2.undistort(image, calib.mtx, calib.dist, None, calib.mtx)

We can see clearly in the below example that the image has been undistorded and looks flat.
<img src="chessboard.png">

Here is an example on the road is: <br>

4. choosing a region of interest to warp/unwarp

The region of interest tries to eliminate the elements that could disturb the lane detection.
It is lower than the horizon and restricted to the center of the left lane, encompassing both lanes on its borders.

5. warp the region of interest

<table>
  <tr>
    <th>original</th>
    <th>warped</th>
  </tr>
  <tr>
    <td><img src="bird_view/persp_transform_original.jpg"></td>
    <td><img src="bird_view/persp_transform_warped.jpg"></td>
  </tr>
  </table>



6. get an histogram and detect left and right lane from histogram


<table>
  <tr>
    <th>detected pixels</th>
    <th>histogram</th>
  </tr>
  <tr>
    <td><img src="assets/histogram.png"></td>
    <td>$<img src="assets/pixels_highlighted.png"></td>
  </tr>
  </table>

7. fit a polynom from the detected lanes

<img src="road_images/frame612_missing top right pixel.png">
8. color the area between the lanes

9. add to the original image and unwarp the combined image

10. calculate the curvature

11. process the video stream

