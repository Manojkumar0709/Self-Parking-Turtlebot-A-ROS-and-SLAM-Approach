# Self-Parking Turtlebot: A ROS and SLAM Approach

An autonomous robotics project where a TurtleBot uses Simultaneous Localization and Mapping (SLAM) and ROS-based navigation to detect a parking space, plan a path, and park itself without manual control.

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [Author](#author)

## Project Overview

This project demonstrates autonomous self-parking behavior on a TurtleBot using ROS (Robot Operating System) and SLAM techniques. The robot builds a map of its environment in real time, localizes itself within that map, detects available parking space, and autonomously navigates into it.

## Problem Statement

Manual robot parking requires constant operator control and is inefficient for real-world automated systems. This project solves that by combining mapping, localization, and path planning so the TurtleBot can identify a parking spot and park itself with minimal human intervention.

## Tech Stack

- **Robot Platform:** TurtleBot3
- **Framework:** ROS / ROS 2
- **Simulation:** Gazebo
- **Visualization:** RViz
- **SLAM:** Cartographer / SLAM Toolbox / Gmapping
- **Navigation:** ROS Navigation Stack / Nav2
- **Programming Language:** Python (rospy / rclpy)
- **Sensors:** LIDAR, odometry, (camera if vision-based detection is used)

## System Architecture

1. **Mapping** — TurtleBot uses SLAM to build a 2D occupancy grid map of the environment using LIDAR data
2. **Localization** — The robot estimates its position within the generated map using particle filter-based localization
3. **Parking Spot Detection** — The system identifies an open parking space using sensor data or predefined markers
4. **Path Planning** — A global and local planner computes a safe trajectory to the parking spot
5. **Motion Control** — The robot executes the planned path and adjusts in real time to obstacles
6. **Parking Completion** — The robot stops once it reaches the target pose within a defined tolerance

## Installation and Setup

Clone the repository:

```bash
git clone https://github.com/Manojkumar0709/Self-Parking-Turtlebot-A-ROS-and-SLAM-Approach.git
cd Self-Parking-Turtlebot-A-ROS-and-SLAM-Approach
```

Install ROS dependencies:

```bash
sudo apt update
sudo apt install ros-<distro>-turtlebot3 ros-<distro>-turtlebot3-simulations
sudo apt install ros-<distro>-slam-toolbox ros-<distro>-navigation2
```

Install Python dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Launch the simulation environment:

```bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

Start SLAM to build the map:

```bash
ros2 launch slam_toolbox online_async_launch.py
```

Run the self-parking node:

```bash
ros2 run self_parking_turtlebot parking_node
```


## Results

- Successfully generated a 2D occupancy grid map of the test environment
- Achieved autonomous localization within the mapped space
- Completed self-parking with defined position and orientation tolerance

## Future Improvements

- Add camera-based visual parking spot detection
- Support dynamic obstacle avoidance during parking
- Extend to multi-spot parking lot scenarios
- Deploy on physical TurtleBot3 hardware for real-world testing

## Author

Manojkumar Mohankumar
[GitHub Profile](https://github.com/Manojkumar0709)
