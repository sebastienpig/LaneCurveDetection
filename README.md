# LaneCurveDetection

## This project aims at detecting lanes on a road and its curvature

Visual includes coloring the surface between the left and the right lanes

Pipeline includes:


<h3> Calibrating the camera </h3>
The calibration of the camera is done through a chessboard view under different angles.
Parameters are saved and used later on.

The parameters are saved in a python object: <br>

<pre>

class calibration:
         
    def __init__(self):
        self.dist=0  # distortion coefficients
        self.mtx=0   #  camera matrix to transform 3D pts to 2D points
        self.rvecs=0 # rotation vector
        self.tvecs=0 # translation vector
    
    def calibrate(self,mtx, dist, rvecs, tvecs):
        self.mtx=mtx   #  camera matrix to transform 3D pts to 2D points
        self.dist=dist  # distortion coefficients
        self.rvecs=rvecs # rotation vector
        self.tvecs=tvecs # translation vector

    def show_parameters(self):
        print ("dist:", self.dist)
        print ("mtx:", self.mtx)
        print ("rvecs:", self.rvecs)
        print ("tvecs:", self.tvecs)
</pre>

First the image is turned into greyed scale, then corner are found using a openCV function to finally gives the points to the <b>cv2.calibrateCamera</b> function. 

<pre>
# Convert to grayscale
        gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
        gray_size = (gray.shape[1], gray.shape[0])
        
        # Find checkboard corners
        ret, corners = cv2.findChessboardCorners(gray, (nx, ny), None)
       
        if ret == True: #matching points were found
        
            # Add points to list
            objpoints.append(objptm)
            imgpoints.append(corners)

            cv2.drawChessboardCorners(img, (nx, ny), corners, ret)
</pre>


<h3> Undistorting the image </h3>
The openCV function used is cv2.undistort(image, calib.mtx, calib.dist, None, calib.mtx)

We can see clearly in the below example that the image has been undistorded and looks flat.
<img src="assets/chessboard.png">

Here is an example on the road is: <br>

We can see that the trees and the mountain have changed, mountain is higher and trees look bigger.
<img src="assets/undistorded_before_after.jpg">


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

