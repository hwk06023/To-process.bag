# To-process.bag
to process .bag (ROS Bag file)
<br/>
<br/>



### Q. What is "ROS Bag file"?
A. "ROS Bag file" contain all data of each stream type(Color, Depth, Infrared)

### Q. What does this program process(handle)?
A. ROS Bag file extracts depth and information of detected objects, PointCloud, Color, etc..


## I. Install ROS

1. Download to [here](https://www.ros.org/blog/getting-started/)

2. In console <br/>
```console
sudo apt-get install python3-roslaunch 
```

```console
sudo apt-get install python3-rosbag 
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




<br/>
<br/>

### Reference
https://dev.intelrealsense.com/docs/python2 <br/>
https://dev.intelrealsense.com/docs/ros-wrapper <br/>
https://dev.intelrealsense.com/docs/opencv-wrapper <br/>
http://wiki.ros.org/rosbag/Code%20API#Python_API 

