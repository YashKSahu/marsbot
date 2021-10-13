# MaRS Bot Navigation 
Jetson Nano powered bot.

## Hardware Requirements
 - Jetson Nano 4GB
 - ....

## Setup
1. export ROS_URI_MASTER http://<jetsonIP>:11311  ->  ~/.bashrc on Jetson Nano
2. export ROS_IP http://<jetsonIP>  ->  ~/.bashrc on Jetson Nano
3. export ROS_URI_MASTER http://<jetsonIP>:11311  ->  ~/.bashrc on BaseStation
4. export ROS_IP http://<baseStationIP>  ->  ~/.bashrc on BaseStation
5. Launch Rosbridge Server (roslaunch robridge_server rosbridge_websocket.launch) on Jetson Nano
