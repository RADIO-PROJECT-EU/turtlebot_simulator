turtlebot_simulator
===================

Launchers for Gazebo simulation of the TurtleBot

# 1. Installation

1.1 Clone the repository into your workspace:

HTTP: git clone -b radio-indigo https://github.com/RADIO-PROJECT-EU/turtlebot_simulator.git

or

SSH: git clone -b radio-indigo git@github.com:RADIO-PROJECT-EU/turtlebot_simulator.git

The branch radio-indigo is the correct one.

1.2 Copy all the gazebo models into your home gazebo models folder (“~./gazebo/models/”):

```
$> cp -rf . ~/.gazebo/models/ from turtlebot_simulator/gazebo/models folder
```

# 2. Examples

## 2.1 Launching FSL map

To run the gazebo world and robot controllers:
```
$> roslaunch turtlebot_gazebo turtlebot_radio.launch
```
To run the ps3 pad controllers (optional):
```
$> roslaunch turtlebot_teleop ps3_teleop.launch
```

## 2.2 Creating a map with gmapping

To create a new map of the environment we can use the package slam_gmapping
```
$> roslaunch turtlebot_gazebo gmapping_radio_demo.launch
```

Move the robot through the map in order to create the map. You can user either the ps3 pad control or other interfaces.

Running RVIZ is useful to see how the map is being created:
```
$> roslaunch turtlebot_gazebo radio_rviz_gmapping.launch
```

To save the map:
```
$> rosrun map_server map_saver -f map_name
```

## 2.3 Navigation and localization with AMCL

The following launch file runs a map server with the map saved previously, runs amcl node for localization and move_base for navigation:
```
$> roslaunch turtlebot_gazebo amcl_radio_demo.launch
```
You can run RVIZ to set the 2D estimated position as well as the 2D navigation goal:
```
$> roslaunch turtlebot_gazebo radio_rviz_amcl.launch
```
Once the 2D estimated position is set, you should move firstly the robot with the pad in order to let amcl improve the pose estimation.






