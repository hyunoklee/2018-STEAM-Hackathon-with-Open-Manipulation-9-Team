## 2018-STEAM-Hackathon-with-Open-Manipulation-9-Team  
9Team  Multi Purpose Master/Slave Robot  
2018 STEAM Hackathon with Open Manipulation 9 Team  

## Training Documents 
http://bitly.kr/bfj8  

## Presentation document 
http://bitly.kr/hSRP  

## Description 
We are 9 Team .   
We use Open Manipulator, ASTRA Camera , Ar Track Marker , Move it and OpenCR packages.   
Our Demo is below flow.   
0 step. Open Manipulator pick up object.   
1 step. Camera recognizes AR marker.   
2 step. I move AR Marker.  
3 step. Open Manipulator moves along the AR Marker movement.  

<img src="/picture/1.png" width="70%" height="70%">  

Click image to link to YouTube video.  
[![Video Label](http://img.youtube.com/vi/HZUmg3MdtU8/0.jpg)](https://youtu.be/HZUmg3MdtU8?t=0s)   

## Dynamixel Setting
We use OpenCR Board and Arduino.   
you can scan Dynamixel Motor by using Examples/OpenCR/08. DynamixelWorkbench/t_Find_Dynamixel/.   
Soure Code is below link .   
https://github.com/ROBOTIS-GIT/OpenCR/blob/beta-test/arduino/opencr_arduino/opencr/libraries/OpenCR/examples/08.%20DynamixelWorkbench/t_Find_Dynamixel/t_Find_Dynamixel.ino  


you can change Dynamixel Motor ID and baudrate by using Examples/OpenCR/08. DynamixelWorkbench/s_monitor .   
Soure Code is below link .   
https://github.com/ROBOTIS-GIT/OpenCR/tree/beta-test/arduino/opencr_arduino/opencr/libraries/OpenCR/examples/08.%20DynamixelWorkbench/s_Monitor  

## OpenCR Setting
We use OpenCR Board and Arduino.   
you install Examples/OpenCR/10.Etc/usb_to_dxl at OpenCR to using ROS .  
Soure Code is below link .  
https://github.com/ROBOTIS-GIT/OpenCR/tree/beta-test/arduino/opencr_arduino/opencr/libraries/OpenCR/examples/10.%20Etc/usb_to_dxl   

## ROS PC Setting
```bash
$ cd ~/catkin_ws/src
$ git clone https://github.com/orbbec/ros_astra_camera.git
$ git clone https://github.com/yhna/ros_astra_launch.git
$ git clone https://github.com/yhna/open_manipulator_ar_tracker.git
$ sudo apt-get install ros-kinetic-rgbd-launch ros-kinetic-libuvc-camera
$ sudo apt-get install ros-kinetic-ar-track-alvar ros-kinetic-ar-track-alvar-msgs  
```
```bash
$ git clone -b beta-test https://github.com/ROBOTIS-GIT/open_manipulator.git
$ git clone -b beta-test https://github.com/ROBOTIS-GIT/robotis_manipulator.git
$ git clone -b beta-test https://github.com/ROBOTIS-GIT/open_manipulator_msgs.git
$ git clone -b master https://github.com/ROBOTIS-GIT/DynamixelSDK.git
$ git clone -b beta-test https://github.com/ROBOTIS-GIT/dynamixel-workbench
$ git clone -b beta-test https://github.com/ROBOTIS-GIT/dynamixel-workbench-msgs
$ sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-moveit* ros-kinetic-industrial-core 
$ sudo apt-get install ros-kinetic-ar-track-alvar ros-kinetic-ar-track-alvar-msgs 
```
```bash
$ git clone https://github.com/hyunoklee/2018-STEAM-Hackathon-with-Open-Manipulation-9-Team.git
$ cp -r ~/catkin_ws/src/2018-STEAM-Hackathon-with-Open-Manipulation-9-Team/src/open_manipulator_example.cpp ~/catkin_ws/src/open_manipulator/open_manipulator_example/src  
$ cp -r ~/catkin_ws/src/2018-STEAM-Hackathon-with-Open-Manipulation-9-Team/src/open_manipulator_example.h ~/catkin_ws/src/open_manipulator/open_manipulator_example/include  
```
```bash
$ cd ~/catkin_ws && catkin_make  
$ roscd astra_camera && ./scripts/create_udev_rules  
```

## Permission Setting about usb of Camera  and usb OpenCR. 
Change OpenCR usb_port in the below file  
~/cw/src/open_manipulator/open_manipulator_controller/open_manipulator_controller.launch   
Change permission about Camera  
```bash
$ sudo chmod 777 /dev/bus/usb/001/*  
```

## Camera Calibration 
```bash
$ rosdep install camera_calibration
$ rosrun camera_calibration cameracalibrator.py --size 7x5 --square 0.030 image:=/camera/rgb/image_raw camera:=/camera/rgb
```

## Run
```bash
$ roscore
$ roslaunch astra_launch astrapro.launch
$ roslaunch open_manipulator_ar_tracker open_manipulator_ar_tracker.launch
$ roslaunch open_manipulator_controller open_manipulator_controller.launch 
$ rosrun open_manipulator_example  open_manipulator_example
```
 
