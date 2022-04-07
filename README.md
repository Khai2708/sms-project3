# sms-course-projects


- Clone the repository 
```bash
ros@ubuntu:~/catkin_ws/project1_ws$ git clone "https://github.com/online-courses-materials/sms-course-projects.git"
```

- Run the rosecore in the command line
```bash
ros@ubuntu:~/catkin_ws/project1_ws$ roscore
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
ros@ubuntu:~/catkin_ws/project1_ws$ catkin_make
```
- Run the subscriber node in the new tab
```bash
ros@ubuntu:~/catkin_ws/project1_ws$ source devel/setup.bash
ros@ubuntu:~/catkin_ws/project1_ws$ rosrun project1 subscriber 
[ INFO] [1649136189.572747064]: Hello World 2
[ INFO] [1649136189.772282120]: Hello World 3
[ INFO] [1649136189.972430143]: Hello World 4
[ INFO] [1649136190.172334747]: Hello World 5
```
- Run the publisher node in the new tab
```bash
ros@ubuntu:~/catkin_ws/project1_ws$ source devel/setup.bash
ros@ubuntu:~/catkin_ws/project1_ws$ rosrun project1 publisher
[ INFO] [1649136189.171565980]: Publisher Node Started
```
