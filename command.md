```
## 

commands used to execute the mapping, saving etc
```

Launching

```
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py

```

cartographer

```
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim:=True

```

saving

```
ros2 run nav2_map_server map_saver_cli -f maps2/my_map2
```

Using keyboard

```
ros2 run turtlebot3_teleop teleop_keyboard

```

run the command to use the map and turtlebot3

FOR HOUSE LAUNCH:

```
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py

```

Now that the map is saved, it needs to be used for navigation from point A to point B.

Now start with navigation

First install

```
sudo apt install ros-humble-rmw-cyclonedds-cpp
```

then export the env variable

```
export RMW_IMPLEMENTATION=rmw_cyclonedds
# Then source your ROS 2 installation
source /opt/ros/humble/setup.bash
```

ALL RUNNING RVIZ AND GAZEBO ENVS:

```
ps aux | grep -E "(rviz|gazebo)" | grep -v grep
```

then kill using

```
kill -9 xxxx
```

Without an accurate map it is hard for the robot to navigate through to set points.

## Is LLM used for navigation?

How is multi robot SLAM and navigation handled?

Will Humanoid be using a map traced from some other means? Say a drone map? Then it is used later for by the humanoid?


There is a cost map associated with the robot navigation. For areas that it can bump into, the cost map is high and so is the neighbouring lines surrounding it. 

Global vs local planner

Global planner: GPS

Local: How to turn, local turn etc.

Make own decisions.

##TF chapter commands

In short there are 3 relationships between the different frames:
 
1. map
2. odom
3. base_footprint

map to base_footprint (can jump although stable in the long run)
Using the map to determine the base_footprint location.

odm -Odometry (estimation of robot position using robot wheel positions)

Odom to base frootprint: Gives error buildup

In ROS2 there can only be one parent- cannot have 2 footprints. 

Prints the relationship: frames_2025-09-27_20.29.02.pdf

``` ros2 run tf2_tools view_frames```



