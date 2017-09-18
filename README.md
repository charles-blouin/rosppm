# rosppm (quadcopter_control)

rosppm is a ROS package which enables ROS to interface with an mcu that generates ppm signal to interface with an RC transmitter.
This is a version modified to received values and publish them as quickly as possible. 

## Features
- Transmit Channel values to the transmitter using the trainer port

## Hardware
Currently tested transmitters follow as below, but in principle will be compatible with most ppm compatible transmitters when followed proper wiring.

More instructions are presented in the following [link](https://404warehouse.net/2016/07/13/rosppm-ros-package-for-accessing-rc-transmitters/)

## Running the code

```
roscore
rosrun rosserial_python serial_node.py _port:=/dev/ttyACM1 _baud:=115200
rostopic pub --once /rosppm_arduino/set_ppm rosppm/ppm_io '{header: auto, a: 1.0, b: 0.5, c: 0., d: 0., e: 0., f: 0., g: 0., h: 0., i: 1.}'
```



##Install
### Installing Dependencies
- rosserial

To run rosppm package rosserial is used to allow the mcu to communicate with roscore
```
sudo apt-get install ros-{ROS-DISTRO}-rosserial-arduino
sudo apt-get install ros-{ROS-DISTRO}-rosserial
```
Tutorial for rosserial can be found in the [rosserial wiki](http://wiki.ros.org/rosserial_arduino/Tutorials/Arduino%20IDE%20Setup)
rosppm is using custom messages. You need to follow the rosserial tutorial to setup your arduino IDE.

### Installing rosppm
Install rosppm package by placing the code in the source folder in catkin_ws

```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws
catkin init

cd ~/catkin_ws/src
git clone https://github.com/charles-blouin/rosppm
cd ~/catkin_ws
catkin_make --pkg rosppm
```
