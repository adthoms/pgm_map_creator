# pgm_map_creator

Create pgm map from Gazebo world file for ROS localization

## Environment

Tested on Ubuntu 20.04, ROS Noetic, Boost 1.71

## Install

Use the following commands to download and compile the package:
```bash
cd ~/catkin_ws/src
git clone https://github.com/adthoms/pgm_map_creator
cd ..
catkin build
```

## Usage

1. Add a `*.world` file to the world folder and include the line:
```
<plugin filename="libcollision_map_creator.so" name="collision_map_creator"/>
```
at the end of the world file before the `</world>` tag.

2. Open a terminal and run:
```bash
cd ~/catkin_ws/src
gzserver src/pgm_map_creator/world/<map file>
```
you should see:
```
Subscribing to: ~/collision_map/command
```

3. Open another terminal and run:
```bash
roslaunch pgm_map_creator request_publisher.launch \
  xmin:=-15 \
  xmax:=15 \
  ymin:=-15 \
  ymax:=15 \
  scan_height:=5 \
  resolution:=0.01
```
Wait for the plugin to generate map. It will be located in the map folder.

## Edits
You can edit the map in an external software like [GIMP](https://www.gimp.org/). 

## Todo
- generation of the YAML file
- options through command line
