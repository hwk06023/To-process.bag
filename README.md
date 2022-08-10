# To-process.bag
to process .bag (ROS Bag file)
<br/>
<br/>

### My Ddevelopment environment
|Info||
|:---:|:---:|
|Camera Model|D455|Required Info
|Operating System & Version|Ubuntu 20.04|
|Platform|PC|
|SDK Version|2.0|
|Language|Python|

<br/>
<br/>

### Q. What is "ROS Bag file"?
A. "ROS Bag file" contain all data of each stream type(Color, Depth, Infrared)

### Q. What does this program process(handle)?
A. ROS Bag file extracts depth and information of detected objects, PointCloud, Color, etc..


## I. Install ROS & pyrealsense2

1. Download to [here](https://www.ros.org/blog/getting-started/)

2. In console <br/>
```console
sudo apt-get install python3-roslaunch 
```

```console
sudo apt-get install python3-rosbag 
``` 

```console
pip3 install -U bagpy
```

<br/>

```console
pip3 install pyrealsense2
```

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
https://jmscslgroup.github.io/bagpy/index.html
