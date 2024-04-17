# Intel-RealSense-D455-and-Unitree-Go1-Navigation
This project deploy uses Intel RealSense D455 camera to deploy Visual SLAM on Unitree Go1 Robot.

We are still editing this page.

### Hardware
1. 1x Unitree Go1 Robot Education (Jetson Nano Version) set
2. 1x Raspberry Pi 4B
3. 1x SD Card
4. 1x mini HDMI to HDMI cable
5. 1x HDMI cable
6. 1x TP-Link TL-WN722N 150Mbps High Gain Wireless USB Adapter (This is essential)
7. Ethernet Cable

### Platform
The main board of this project is the Jetson Nano on the Unitree Go1 robot, with IP Address 192.168.123.15 (will explain this after).
Operating System: Ubuntu 18.04
ROS Version: Melodic

## Image Transfer
With the trasfer speed limitation of USB 2.1 port on Go1, we need to find alternative to send image from Intel RealSense D455 to the Jetson Nano. Our team decided to use an external Raspberry Pi 4B(8G) to connect to the Intel RealSense D455 camera and send the captured data to Go1's Jetson Nano through ethernet cable. Therefore, we have a master-slave structure in our system.

ROS Master: Jetson Nano
ROS Slave: Raspberry Pi 4B

### ROS: Master-Slave Clock Synchronization
Our systme uses "chrony" packages. To install it, open the terminal and type:
```
sudo apt install chrony
```

### ROS: Master-Slave Communication
On Jetson Nano:
```
export ROS_MASTER_URI=http://192.168.123.15:11311
export ROS_HOSTNAME=192.168.123.15
roscore
```
On Raspberry Pi:
```
export ROS_MASTER_URI=http://192.168.123.15:11311
export ROS_HOSTNAME=192.168.123.87
```
