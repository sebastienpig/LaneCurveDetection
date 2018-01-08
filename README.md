# LaneCurveDetection

## This project aims at detecting lanes on a road and its curvature

Visual includes coloring the surface between the left and the right lanes

Pipeline includes:

1. acquiring image

2. filtering the image

3. undistorting the image

4. choosing a region of interest to warp/unwarp

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

