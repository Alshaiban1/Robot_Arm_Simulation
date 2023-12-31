## Robot Arm Simulation
The robot arm packages provided in the repository https://github.com/smart-methods/arduino_robot_arm were used to run a simulation of the robot arm in RViz and Gazebo.
The uploaded images are the screenshots of the simulation on a virtual box running ROS melodic on ubuntu 18.04.

## ROS installation
For windows and mac users, it is better to install ROS on ubuntu using a virtual machine.

1. Download VirtualBox 
https://www.virtualbox.org/wiki/Downloads

1. Download appropriate ubuntu image (ubuntu 18.04 was used)
https://releases.ubuntu.com/

1. Create the virtual machine
https://help.ubuntu.com/community/Installation/SystemRequirements

1. Install Terminator to utilize multiple terminals on the same window (optional)
Write in the terminal
```
sudo apt install terminator
```

1. Install ROS
https://wiki.ros.org/ROS/Installation

1. For installing ROS melodic on ubuntu 18.04 follow these steps
http://wiki.ros.org/melodic/Installation/Ubuntu


## Prepare ROS for simulation

1. Create a workspace by using catkin_make
http://wiki.ros.org/catkin/Tutorials/create_a_workspace 

1. Install the package arduino_robot_arm
- Add the “arduino_robot_arm” package to “src” folder
```
	$ cd ~/catkin_ws/src
	$ sudo apt install git
	$ git clone https://github.com/smart-methods/arduino_robot_arm
```
- Install all the dependencies
```
	$ cd ~/catkin_ws
	$ rosdep install --from-paths src --ignore-src -r -y
	$ sudo apt-get install ros-melodic-moveit
	$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
	$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
	$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
```
- Compile the package
```
$ catkin_make
```


## Simulation

1. Launch robot arm on RViz
```
$ roslaunch robot_arm_pkg check_motors.launch
```
1. Launch robot arm on Gazebo
```
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
```
1. Python script to transfer data from RViz to Gazebo
```
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
```
1. Change the permission for python script
```
	$ cd catkin_ws/src/arduino_robot_arm/robot_arm_pkg/scripts
	$ sudo chmod +x joint_states_to_gazebo.py
```

 ## Terminator terminals and simulation images

 - Terminals
 <img width="1151" alt="Robot Arm Simulation Terminal" src="https://github.com/Alshaiban1/Robot_Arm_Simulation/assets/139134530/c8b555cb-0d65-4635-806a-9c5d5325c82f">

- Robot arm at rest
<img width="1145" alt="Robot Arm Simulation Resting Position" src="https://github.com/Alshaiban1/Robot_Arm_Simulation/assets/139134530/74fdc112-d2d8-454b-8ea0-3051347f7a9a">


- Robot arm moved
<img width="1149" alt="Robot Arm Simulation" src="https://github.com/Alshaiban1/Robot_Arm_Simulation/assets/139134530/47b38763-de49-43a8-90aa-0cca9812c30b">

 


