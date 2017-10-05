# Connect the cameras
Make sure the camera's are connected to /dev/video1 && /dev/video2 
(otherwise change this in the config files usb_cam-set.launch && usb_cam-set-record.launch )


# to launch The cameras and stream the video to the display to check the set-up:
roslaunch usb_cam-set.launch 


# to callibrate the cameras use: (Note: make sure you stream the camera's as above before starting)
rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.02517 right:=/camera1/usb_cam1/image_raw left:=/camera2/usb_cam2/image_raw right_camera:=/usb_cam1 left_camera:=/usb_cam2 --approximate=0.001 --no-service-check 


# to launch The camera's and saving the footage to '~/.ros/' as left.avi and right.avi :
roslaunch usb_cam-set-record.launch 

# TIP: for converting .avi to jpegs (Replace between tags):
ffmpeg -i {{FILENAME}}.avi -f image2 {{OUTPUT_FOLDER}}/image-%03d.jpg

