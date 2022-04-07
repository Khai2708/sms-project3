# sms-course-projects

- Creating the projects 
```bash
ros@ubuntu:~/catkin_ws$ mkdir project3_ws
ros@ubuntu:~/catkin_ws$ cd project3_ws/
ros@ubuntu:~/catkin_ws/project3_ws$ mkdir src
ros@ubuntu:~/catkin_ws/project3_ws$ cd src
ros@ubuntu:~/catkin_ws/project3_ws/src$ catkin_create_pkg project3 roscpp
Created file project3/package.xml
Created file project3/CMakeLists.txt
Created folder project3/include/project3
Created folder project3/src
Successfully created files in /home/ros/catkin_ws/project3_ws/src/project3. Please adjust the values in package.xml.
ros@ubuntu:~/catkin_ws/project3_ws/src$ cd ..
---------------------------------------------------------------
UPDATE src FOLDER CPP CODES (speed_calc.cpp & rpm_pub.cpp) AND C_MAKE FILE (add target information for building speed_calc & rpm_pub objects )
---------------------------------------------------------------
ros@ubuntu:~/catkin_ws/project3_ws$ catkin_make
Base path: /home/ros/catkin_ws/project3_ws
Source space: /home/ros/catkin_ws/project3_ws/src
Build space: /home/ros/catkin_ws/project3_ws/build
Devel space: /home/ros/catkin_ws/project3_ws/devel
Install space: /home/ros/catkin_ws/project3_ws/install
####
#### Running command: "make cmake_check_build_system" in "/home/ros/catkin_ws/project3_ws/build"
####
####
#### Running command: "make -j4 -l4" in "/home/ros/catkin_ws/project3_ws/build"
####
Scanning dependencies of target speed_calc
[ 50%] Built target rpm_pub
[ 75%] Building CXX object project3/CMakeFiles/speed_calc.dir/src/speed_calc.cpp.o
[100%] Linking CXX executable /home/ros/catkin_ws/project3_ws/devel/lib/project3/speed_calc
[100%] Built target speed_calc
ros@ubuntu:~/catkin_ws/project3_ws$ 
```
- Clone the repository 
```bash
ros@ubuntu:~/catkin_ws$ mkdir project3_ws
ros@ubuntu:~/catkin_ws/project3_ws$ cd ..
ros@ubuntu:~/catkin_ws/project3_ws$ git clone "https://github.com/online-courses-materials/sms-project3.git"
```

- Run the rosecore in the command line
```bash
ros@ubuntu:~/catkin_ws/project3_ws$ roscore
.. logging to /home/ros/.ros/log/2eef3038-b49f-11ec-8a39-8b31e70de496/roslaunch-ubuntu-2895.log
Checking log directory for disk usage. This may take a while.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://ubuntu:36287/
ros_comm version 1.15.13


SUMMARY
========

PARAMETERS
 * /rosdistro: noetic
 * /rosversion: 1.15.13

NODES

auto-starting new master
process[master]: started with pid [2906]
ROS_MASTER_URI=http://ubuntu:11311/

setting /run_id to 2eef3038-b49f-11ec-8a39-8b31e70de496
process[rosout-1]: started with pid [2918]
started core service [/rosout]
```
- Compile the project
```bash
ros@ubuntu:~/catkin_ws/project3_ws$ catkin_make
```
- Run the subscriber node in the new tab
```bash
ros@ubuntu:~/catkin_ws/project3_ws$ source devel/setup.bash
ros@ubuntu:~/catkin_ws/project3_ws$ rosrun project3 rpm_pub 
[ INFO] [1649314968.240842642]: Publishing RPM...
```
- Run the publisher node in the new tab
```bash
ros@ubuntu:~/catkin_ws/project3_ws$ source devel/setup.bash
ros@ubuntu:~/catkin_ws/project3_ws$ rosrun project3 speed_calc 
[ WARN] [1649315004.745731757]:  No Value set for wheel_radius server parameter.
[ WARN] [1649315004.846294322]:  No Value set for wheel_radius server parameter.
[ WARN] [1649315004.945176571]:  No Value set for wheel_radius server parameter.

```
- Test changing wheel_radius parameter   in the new tab
```bash
ros@ubuntu:~/catkin_ws/project3_ws$ rosparam list
/rosdistro
/roslaunch/uris/host_ubuntu__39201
/rosversion
/run_id
ros@ubuntu:~/catkin_ws/project3_ws$ rosparam set wheel_radius 0.75
ros@ubuntu:~/catkin_ws/project3_ws$ rosparam set wheel_radius 0.86
ros@ubuntu:~/catkin_ws/project3_ws$ rosparam list
/rosdistro
/roslaunch/uris/host_ubuntu__39201
/rosversion
/run_id
/wheel_radius
ros@ubuntu:~/catkin_ws/project3_ws$

os@ubuntu:~/catkin_ws/project3_ws$ rostopic list
/rosout
/rosout_agg
/rpm
/speed
ros@ubuntu:~/catkin_ws/project3_ws$ rostopic echo rpm
data: 60.0
---
data: 60.0
---
data: 60.0
ros@ubuntu:~/catkin_ws/project3_ws$ rostopic list
/rosout
/rosout_agg
/rpm
/speed
ros@ubuntu:~/catkin_ws/project3_ws$ rostopic echo speed
data: 5.403534889221191
---
data: 5.403534889221191
---
data: 5.403534889221191
---
data: 5.403534889221191  ( Value of speed changed after setting a new value for wheel_radius parameter)
---
data: 0.7853975296020508
---
data: 0.7853975296020508

```
