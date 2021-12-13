# MaRS Bot Navigation 
Jetson Nano powered bot.

## Hardware Requirements
 - Jetson Nano 4GB Developer Kit
 - Power Bank, ~5V/2A (to power Nano)
 - MPU 9250/9050/6050 IMU module

## Hardware Setup
 - Preparing Nano
   1. Flash latest jetpack on a micro-sdcard, insert the card and power up Nano
   2. Disconnect the J48 jumper to power nano via micro-USB port
   3. Connect USB-A of power bank to micro-USB B of Nano to power it UP!
   4. Set Nano to 5W(power saving) mode before deploying
   5. Insert the wifi-adapter and connect Nano to a LAN
   6. Note down the Nano's IP address(will be used furhter for SSH and ROS_MASTER_URI):
   ```
   $ hostname -I
   ```
 - IMU
   - Connections:

   | IMU | Jetson Nano  |
   |-----|--------------|
   | VCC | pin 17 (3.3V)|
   | GND | pin 25 (GND) |
   | SCL | pin 5 (SCL)  |
   | SDA | pin 3 (SDA)  |
   1. VCC of the IMU to pin 17 (3.3V) of the Jetson Nano
   2. GND of the IMU to pin 25 (GND) of the Jetson Nano
   3. SCL of the IMU to pin 5 (SCL) of the Jetson Nano
   4. SDA of the IMU to pin 3 (SDA) of the Jetson Nano

   - *Note: Check the IMU's orientation before fixing it on the chassis

 - Connect Arduino cable to Nano

## Setup
  1. Add or modify following lines into the .bashrc file on Nano:
     - export ROS_URI_MASTER http://<Nano's IP>:11311
     - export ROS_IP http://<Nano's IP>
  2. Connect basestation to the same LAN on which Nano is connected
  3. SSH into Nano via its previous noted IP address
  ```
  $ sudo ssh -X mars@<Nano's IP>
  ```
  4. Launch Rosbridge Server on Jetson Nano
   ```
   $ roslaunch robridge_server rosbridge_websocket.launch
   ```
  5. Launch the IMU publisher Node on Nano
   ```
   $ roslaunch imu_package imu.launch
   ```
  6. Add or modify following lines into the .bashrc file on BaseStation:
     - export ROS_URI_MASTER http://<Nano's IP>:11311
     - export ROS_IP http://<BaseStation's IP>
  7. Launch rosserial node on Nano
   ```
   $ roslaunch rosserial_python serial.launch /dev/ttyUSB0
   ```
  8. Launch marsbot
   ```
   $ roslaunch marsbot marsbot.launch
   ```
  9. Operate 
  
