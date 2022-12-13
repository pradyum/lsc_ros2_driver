# Autonics LSC ROS2 Driver
This ROS2 Driver is for Autonics LSC Series

### Table of Contents

- [Supported Hardware](#1-supported-hardware)
- [ROS API](#2-ros-api)
- [Installation](#3-installation)
- [Start](#4-start)


### 1. Supported Hardware
#### 1.1 Model name : LSC Series
#####   Website : [Autonics/LiDAR/LSC](https://www.autonics.com/series/3001018)


### 2. ROS API
#### 2.1 Published Topics
* scan(sensor_msgs/LaserScan) : Scan data from the device
* diagnostics(diagnostic_updater) : Scan topic status
#### 2.2 Parameters
##### 2.2.1 Dynamic
* addr(default : 192.168.0.1, type : string) - The device ip address
* port(default : 8000, type : string) - The port number of device
* frame_id(default : laser, type : string) - The frame name of scan data
* range_min(default : 0.05, type : double) - Minimum range value [m]
* range_max(default : 25.0, type : double) - Maximum range value [m]
* intensities(default : true, type : string) - A flag to choose whether putting intensities information into topic message
* pub_topic(default : scan. type : string) - The name of published topic
##### 2.2.2 Static
* diagnostics_tolerance(default : 0.1, type : double) - Tolerance of topic frequency
* diagnostics_windows_time(default : 1, type : int) - Number of events to consider in the statics 


### 3. Installation
####   3.1 from source
##### 3.1.1 LINUX
    source /opt/ros/$ROS_DISTRO/setup.bash
    mkdir -p ~/colcon_ws/src 
    cd ~/colcon_ws 
    colcon build --symlink-install
    source ~/colcon_ws/install/local_setup.bash
    cd ~/colcon_ws/src 
    git clone https://github.com/AutonicsLiDAR/lsc_ros2_driver.git
    
    sudo apt update 
    sudo apt install ros-$ROS_DISTRO-diagnostic-updater

    cd ~/colcon_ws 
    colcon build --packages-select lsc_ros2_driver --event-handlers console_direct+
    
    source ~/colcon_ws/install/local_setup.bash
    
    
##### 3.1.2 WINDOWS
    #foxy
    C:\dev\ros2_foxy\local_setup.bat
    mkdir -p C:\dev\colcon_ws\src 
    cd C:\dev\colcon_ws
    colcon build --symlink-install
    C:\dev\colcon_ws\install\local_setup.bat
   
    cd C:\dev\colcon_ws\src
    git clone https://github.com/AutonicsLiDAR/lsc_ros2_driver.git
    git clone https://github.com/ros/diagnostics.git -b foxy
    cd C:\dev\colcon_ws
    
    colcon build --packages-select diagnostic_updater --event-handlers console_direct+
    colcon build --packages-select lsc_ros2_driver --event-handlers console_direct+
    
    C:\dev\colcon_ws\install\local_setup.bat
    
    
    #humble
    C:\dev\ros2_humble\local_setup.bat
    mkdir -p C:\dev\colcon_ws\src 
    cd C:\dev\colcon_ws
    colcon build --symlink-install
    C:\dev\colcon_ws\install\local_setup.bat
    
    cd C:\dev\colcon_ws\src
    git clone https://github.com/AutonicsLiDAR/lsc_ros2_driver.git
    git clone https://github.com/ros/diagnostics.git -b humble
    cd C:\dev\colcon_ws
    
    colcon build --packages-select diagnostic_updater --event-handlers console_direct+
    colcon build --packages-select lsc_ros2_driver --event-handlers console_direct+
    
    C:\dev\colcon_ws\install\local_setup.bat
   
   
####   3.2 from binary
    sudo apt install ros-$ROS_DISTRO-lsc-ros2-driver


### 4. Start
    ros2 launch lsc_ros2_driver lsc_ros2_driver_launch.py
