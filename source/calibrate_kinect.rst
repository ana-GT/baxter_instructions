Calibrate Kinect
================

0. Remember that in all terminals you open you must run baxter.sh (with
   the IP information from the robot and from the workstation updated).

   .. code-block:: bash

      roscd
      cd ..
      . baxter.sh

1. Open the left camera at resolution 1280x800
   
   .. code-block:: bash

      rosrun baxter_tools camera_control.py -o left_hand_camera -r 1280x800

2. Run a freenect launch to read Kinect information:

   .. code-block:: bash

      roslaunch freenect_launch freenect-registered-xyzrgb.launch

   Leave this running during the whole calibration process.

3. If you want to check that the camera and the Kinect are working, you can check out their image
   outputs:

   .. code-block:: bash

      rosrun image_view image_view image:=/cameras/left_hand_camera/image
      rosrun image_view image_view image:=/camera/rgb/image_color

   Make sure you can see the 3 markers from both image flows.

4. Since both your Kinect and the camera are working, now you can run the calibration code:

   .. code-block:: bash

      roslaunch baxter_kinect_calibration baxter_bundle_calibrate.launch

   Move the markers a little bit on the table to give more input to the bundler.

5. To store the transformation: You can store the relative transformation of the camera
   ( camera\_link) with respect to any parent node. In my case, I store it with respect to torso:

   .. code-block:: bash

      rosrun tf tf_echo torso camera_link

   You will get a constant flow of the transformation of the Kinect to the torso
   in x, y, z, roll, pitch, yaw.

6. Additional note: If you want to see what other relative transforms you can get:

   .. code-block:: bash

      rosrun tf view_frames

   This will store a pdf with a diagram showing the frames and their relative 
   connection, so you can select other reference frames for the camera.
