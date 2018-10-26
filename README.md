![alt text](https://raw.githubusercontent.com/easily-distracted/spin-ydlidar/master/Building-5-Tower.png)


# spin_ydlidar 
This repository contains code to control a Dynamixel motor and a 2D YDLIDAR LiDAR to create a 3D point cloud that can be visualized in rviz.


# Setup Directions
1. Create Catkin Workspace
2. Source required repos
  https://github.com/easily-distracted/spin_ydlidar.git
  https://github.com/EAIBOT/ydlidar.git
  https://github.com/arebgun/dynamixel_motor.git
3. Run catkin_make
4. In the tutorials/launch folder, update the basic_motors.launch file, go to line 12. These parameters are used to set up the dynamixel_motor package. In particular, make sure the port_name and baud_rate match your servo. Also, check that your motor id falls within the inclusive range from min_motor_id to max_motor_id. 
5. Save and compile changes (if applicable).<br/>
```roslaunch spin_ydlidar basic_motors.launch```<br/>
6. In a new terminal, open the rostopics list.  There should be two new commands: /tilt_controller/command and /tilt_controller/state.  /command will issue new positions to the motor via Float64 (try this using rostopic pub).  /state will list various pieces of information about the motor (rostopic echo).
7. If this is fully functional, kill the node and do:<br/>
```roslaunch spin_ydlidar tilting_continuous.launch```<br/>
This should cause the motor to regularly sweep from 90 to -90 and generate a point cloud.
Be sure to update the dynamixel_servos_tilting.yaml for position, speed, etc.

## Possible Dynamixel Errors
Is the USB properly inserted and setup for your computer?  
Is the Dynamixel connected to a 12V power source via the adapter?  
Is the switch on the USB adapter at the proper loaction?  

# Acknowledgements
Based heavily of works created here: </br>
https://github.com/RobustFieldAutonomyLab/spin_hokuyo

Inspired by the work seen here: </br>
https://github.com/gcc-robotics/3d_photobooth/blob/master/CapstoneFinalReport_VisionTeam.pdf </br>

## Dynamixel Control
The class system used to control the Dynamixel motors and the basis for the servo template were based on the examples provided in Chap. 8 of "Effective Robotics Programming with ROS - Third Edition" by Anil Mahtani, Luis Sanchez, Enrique Fernandea, and Aaron Martinez.
##
## pcl_assembler_client
The pcl_assembler_client is a modified form of the periodic_snapshotter.cpp which is included in the /examples folder of laser_assembler which is hosted at:
https://github.com/ros-perception/laser_assembler
##

# Rework Authors #

Reece Holland
