# ORB-SLAM3 Set-Up in ROS Catkin Workspace (Ubuntu 20.04 & ROS Noetic)

This guide provides instructions for setting up the ORB-SLAM3 package in a ROS workspace. Note that this guide is specifically written for the Ubuntu 20.04 ROS Noetic distribution. 

### Prerequisites:
Please make sure these are appropriately set-up prior to continuing with the rest of these instructions: 
- Ubuntu 20.04
- ROS Noetic installed
- ROS Catkin workspace set up

## Install System Dependencies
sudo apt install -y build-essential cmake git \
sudo apt install -y libgtk-3-dev libgl1-mesa-glx libgl1-mesa-dev libglew-dev \
sudo apt install -y libeigen3-dev libboost-dev libsuitesparse-dev

## Clone ORB-SLAM3 Repository
cd ~/catkin_ws/src \
git clone https://github.com/UZ-SLAMLab/ORB_SLAM3.git 

## Compile ORB-SLAM3 Third-Party Dependencies
cd ~/catkin_ws/src/ORB_SLAM3/Thirdparty/DBoW2 \
mkdir build && cd build \
cmake ..

## g2o
cd ~/catkin_ws/src/ORB_SLAM3/Thirdparty/g2o \
mkdir build && cd build \
cmake ..

## Pangolin
cd ~/catkin_ws/src/ORB_SLAM3/Thirdparty/Pangolin \
mkdir build && cd build \
cmake ..

## Build ORB-SLAM3
cd ~/catkin_ws/src/ORB_SLAM3 \
mkdir build && cd build \
cmake ..

## Set Up ROS Package for ORB-SLAM3
cp -r ~/catkin_ws/src/ORB_SLAM3/Examples/ROS/ORB_SLAM3 ~/catkin_ws/src/

## Build Catkin Workspace
cd ~/catkin_ws \
catkin_make

## Source the Workspace
source ~/catkin_ws/devel/setup.bash
