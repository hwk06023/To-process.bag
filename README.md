# To-process.bag
to process .bag (ROS Bag file)
<br/>
<br/>

### My Ddevelopment Environment
|Info||
|:---:|:---:|
|Camera Model|D455|Required Info
|Operating System & Version|Ubuntu 20.04|
|Platform|PC|
|SDK Version|2.0|
|Language|Python|

<br/>

### Q. What is "ROS Bag file"?
A. "ROS Bag file" contain all data of each stream type(Color, Depth, Infrared)

### Q. What does this program process(handle)?
A. ROS Bag file extracts depth and information of detected objects, PointCloud, Color, etc..


## I. Install Library

### ROS 1

1. Download to [here](https://www.ros.org/blog/getting-started/)

2. In console 
```console
sudo apt-get install python3-roslaunch 
```

```console
sudo apt-get install python3-rosbag 
``` 

<br/>

### ROS 2

1. Set locale  

```console
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

2. Add the ROS 2 apt repository 

```console
sudo apt install software-properties-common

sudo add-apt-repository universe
```

```console
sudo apt update && sudo apt install curl gnupg lsb-release

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

```console
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

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

## II. Rosbag API in python3

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


## III. Bag file to Depth bag file

```python


```


<br/>
<br/>

## IV. Point Cloud

```python


```


<br/>
<br/>

### Reference
https://dev.intelrealsense.com/docs/python2 <br/>
https://dev.intelrealsense.com/docs/ros-wrapper <br/>
https://dev.intelrealsense.com/docs/opencv-wrapper <br/>
http://wiki.ros.org/rosbag/Code%20API#Python_API <br/>
http://wiki.ros.org/rosbag/Commandline <br/>
https://jmscslgroup.github.io/bagpy/index.html <br/>
https://docs.ros.org/en/rolling/Installation/Alternatives/Ubuntu-Development-Setup.html
