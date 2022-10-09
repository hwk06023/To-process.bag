# To-process.bag
to process .bag (ROS Bag file)
<br/>
<br/>

### My Ddevelopment Environment
|Info||
|:---:|:---:|
|Using device|RealSense(D455), Multipleye
|Operating System & Version|Ubuntu 20.04|
|Platform|PC|
|SDK Version|2.0|
|Language|Python|

<br/>

### Q. What is "ROS Bag file"?
A. "ROS Bag file" contain all data of each stream type(Color, Depth, Infrared)

### Q. What does this program process(handle)?
A. ROS Bag file extracts depth and information of detected objects, PointCloud, Color, etc..

<br/>
<br/>

## I. Install Library

### ROS 1
#### noetic

1. Setup your sources.list
```console
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

<br/>

2. Set up your keys
```console
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

<br/>

3. Installation

First, make sure your Debian package index is up-to-date:
```console
sudo apt update
```

<br/>

Now pick how much of ROS you would like to install.

Desktop-Full Install: (Recommended) : Everything in Desktop plus 2D/3D simulators and 2D/3D perception packages

```console
sudo apt install ros-noetic-desktop-full
```

<br/>


Desktop Install: Everything in ROS-Base plus tools like rqt and rviz

```console
sudo apt install ros-noetic-desktop
```

<br/>

ROS-Base: (Bare Bones) ROS packaging, build, and communication libraries. No GUI tools.

```console
sudo apt install ros-noetic-ros-base
```

<br/>

more packages available in ROS, to find packages

```console
apt search ros-noetic
```

and install (PACKAGE => e.g. slam-gmapping)

```console
sudo apt install ros-noetic-PACKAGE
```

<br/>

4. Environment setup
```
source /opt/ros/noetic/setup.bash(.zsh, ...)
```

<br/>

bash
```console
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

zsh
```console
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```

<br/>


5. Dependencies for building packages

```console
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

<br/>

```console
sudo apt-get install python3-roslaunch 
```

```console
sudo apt-get install python3-rosbag 
``` 

<br/>
<br/>

### ROS 2
#### rolling

1. Set locale  

```console
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

<br/>

2. Add the ROS 2 apt repository 

```console
sudo apt install software-properties-common

sudo add-apt-repository universe
```

<br/>

```console
sudo apt update && sudo apt install curl gnupg lsb-release

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

```console
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

<br/>

3. Downloading ROS 2

```console
sudo apt update && sudo apt upgrade
```

```console
sudo apt install ros-rolling-desktop
```

```console
sudo apt install ros-rolling-ros-base
```

<br/>
<br/>

### Rviz - Ros1
#### noetic

1. Install

```console
sudo apt-get install ros-fuerte-visualization
```

```console
sudo apt-get install ros-noetic-rviz
```

2. Display

```console
source /opt/ros/noetic/setup.bash(.zsh ..)
roscore &
```

```console
rosrun rviz rviz
```

<br/>
<br/>

### Rviz - Ros2
#### foxy

1. Build from Source

```console
sudo apt install ros-foxy-ros-base

sudo apt install ros-foxy-desktop

source /opt/ros/foxy/setup.bash(.zsh)
```


```console
sudo apt-get install ros-foxy-rviz-visual-tools

ros2 launch rviz_visual_tools demo_rviz.launch.py
```

```console
rosdep install --from-paths src --ignore-src --rosdistro foxy
```

<br/>

2. Quick Start Demo

```console
ros2 run rviz_visual_tools
```

<br/>
<br/>

### Bagpy

```console
pip3 install -U bagpy
```

<br/>

### Pyrealsense2

```console
pip3 install pyrealsense2
```

<br/>
<br/>
<br/>

## II. Rviz


```console
rosrun rosbag record -O ~~~.bag /velodyne_packets
```

```console
rosbag play ~~~.bag
```




<br/>
<br/>

## III. Bagpy in Python3

```python
import bagpy
from bagpy import bagreader
import pandas as pd
import numpy as np
```

```python
b = bagreader('[DATA Location]') # load bag file
```

```python
b.topic_table
```

```python
data = b.message_by_topic('[Title in table]')
```

```python
df_out = pd.read_csv(data)
df_out
```

<br/>
<br/>

## IV. Rosbag API in python3

```python
import rosbag
from std_msgs.msg import Int32, String
```

```python
bag = rosbag.Bag('[DATA Location]') # load bag file
```
```python
'''
Use Method
'''
```
```python
bag.close # free bag
```

<br/>
<br/>

## VI. Point Cloud

Console-1

```console
roscore &
```

Console-2

```console
rosbag play --clock [Data] -l
```

[Data] : ex_1.bag, ex_2.bag ...<br/>


Option <br/>
(--clock) : To displaytime <br/>
(-l) : endless repetition <br/>

<br/>

Console-1

```console
rostopic echo /device_0/sensor_0/Depth_0/image/data
```

<br/>
<br/>

## SLAM

[SLAM](https://github.com/hwk06023/SLAM) is still being written.


<br/>
<br/>

### My Device in ROS info

[Multipleye](Multipleye_info.md)
[RealSense](RealSense_info.md)


<br/>
<br/>

### Reference
https://dev.intelrealsense.com/docs/python2 <br/>
https://dev.intelrealsense.com/docs/ros-wrapper <br/>
https://dev.intelrealsense.com/docs/opencv-wrapper <br/>
http://wiki.ros.org/rosbag/Code%20API#Python_API <br/>
http://wiki.ros.org/rosbag/Commandline <br/>
https://jmscslgroup.github.io/bagpy/index.html <br/>
https://docs.ros.org/en/rolling/Installation/Alternatives/Ubuntu-Development-Setup.html <br/>
https://index.ros.org/p/rviz_visual_tools/<br/>
https://index.ros.org/p/example_interfaces/#humble-overview <br/>
https://velog.io/@717lumos/Rviz-Rviz-%EC%8B%9C%EA%B0%81%ED%99%94%ED%95%98%EA%B8%B0-Marker <br/>
