# Navigation Robot in Gazebo

This is a ROS 2-based simulation project where a differential drive robot with a mounted camera navigates in a Gazebo environment. The project demonstrates robot modeling, velocity control using `cmd_vel`, and camera image streaming using plugins.

![navigation_robot_gazebo](https://github.com/Kleo-Fernandes/Navigation_robot_Ros/assets/preview.png)

---

## Packages Overview

- **navigation_robot_description**: Contains URDF/Xacro files and robot configuration.
- **navigation_robot_bringup**: Launch files to start Gazebo simulation with controllers and camera.
- **navigation_robot_control**: Defines and loads differential drive controllers.

---

## Project Description

This robot simulation features a mobile base with differential drive control and an onboard camera for visual feedback. The robot is designed for navigation and perception tasks using ROS 2 and Gazebo.

### Goal

Enable basic motion control using `/cmd_vel` and visualize the camera stream for perception-based navigation experiments.

---

## Key Features

### 1. Differential Drive

- Implemented using `diff_drive_controller`
- Accepts velocity commands from `/cmd_vel`
- Controlled via teleop or autonomous nodes

### 2. Camera Integration

- Simulated using `libgazebo_ros_camera` plugin
- Publishes image data on `/camera/image_raw`
- Suitable for CV tasks using OpenCV or rqt_image_view

---

## Launch Instructions

```bash
# Launch Gazebo simulation
ros2 launch navigation_robot_bringup navigation_robot_gazebo.launch.py

# Send movement commands
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist '{linear: {x: 0.5}, angular: {z: 0.2}}'

# Visualize camera output
rqt_image_view /camera/image_raw
