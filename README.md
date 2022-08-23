# Turtlebot3-with-SLAM
1.What does SLAM mean?
SLAM as abbreviation means "Simultaneous Localization and Mapping".

![image](https://user-images.githubusercontent.com/86796891/186147465-d30fa8f1-6fb5-42c7-b35c-393546cd847c.png)
https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping

2.TURTLEBOT3
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/

![image](https://user-images.githubusercontent.com/86796891/186147566-d56ef30b-7145-425e-a7ff-2fb0e969415e.png)
Burger
![image](https://user-images.githubusercontent.com/86796891/186147615-b4b1a639-d4d0-4d1f-b50a-254d7d528407.png)
Waffle

Turtlebot3 Burger
Type in the commands down below in the terminal:
Install ROS 1 on Remote PC 3. 1. 2
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
$ chmod 755 ./install_ros_melodic.sh 
$ bash ./install_ros_melodic.sh

Install Dependent ROS 1 Packages 3. 1. 3
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
  
  Install TurtleBot3 Packages 3. 1. 4
  $ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3

Enter these codes in the terminal to install Simulation packages Simulation Install 6. 1. 1
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make

new terminal after the 3rd step After you are done type in this command in the terminal
$ source ~/catkin_ws/devel/setup.bash

JUST COPY (ctrl+c) and PASTE (ctrl+v) in Terminal

Run these commands in the terminal to launch the simulation world. Launch Simulation World
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

Run these commands in the terminal to launch the SLAM Node. Run SLAM Node
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

Run this command to be able to interact and control the robot Run Teleoperation Node
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

JUST COPY (ctrl+c) and PASTE (ctrl+v) in Terminal

Now you should be able to control the robot using the keys WASDX to roam around the gazebo simulated map. After you are done exploring the map with your robot you should save

more information visit this website https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/

3.create and save a map
![image](https://user-images.githubusercontent.com/86796891/186148408-675f43b1-3c7d-4952-b425-13d348c57505.png)

![image](https://user-images.githubusercontent.com/86796891/186148447-1a050bed-ff82-4bf5-8e1e-6c2392bc971b.png)
The map before move the robot

control the robot
![image](https://user-images.githubusercontent.com/86796891/186148523-f479e5be-35c7-4b37-a748-b0fa86b7169a.png)

![image](https://user-images.githubusercontent.com/86796891/186148565-83a36b30-283e-481c-a5b5-981c6770c504.png)
To save the map using (Ctrl + Alt + T) Or
$ rosrun map_server map_saver -f ~/map


4.Use another ROS robot with SLAM approach to create and save a map
This ROS package implements SLAM on a 2 wheeled differential drive robot to map an unknown environment. A joystick is used to teleoperate the robot in Gazebo. The map generated is then used for autonomous navigation using the ROS Navigation stack.

Type in the commands down below in the terminal Build package from source: navigate to the source folder of your catkin workspace and build this package using:

$ git clone https://github.com/devanshdhrafani/diff_drive_bot.git
$ cd ..
$ catkin_make
Install Required dependencies:
$ sudo apt-get install ros-melodic-dwa-local-planner
$ sudo apt-get install ros-melodic-joy
Load the robot in the Gazebo environment:
$ roslaunch diff_drive_bot gazebo.launch
Launch the slam_gmapping node. This will also start rviz where you can
visualize the map being created:
$ roslaunch diff_drive_bot gmapping.launch
using keyboard:
$ rosrun diff_drive_bot keyboard_teleop.py
Save the map using:
$ rosrun map_server map_saver -f ~/test_map

Now open the Gazebo and Rviz
![image](https://user-images.githubusercontent.com/86796891/186148817-41249f4c-ba83-43c7-8dae-93341fb0fc86.png)

![image](https://user-images.githubusercontent.com/86796891/186149134-09427a2f-fd05-490c-a737-25f99e198d2c.png)

