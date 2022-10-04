# ecse373_f22_nnm22_lab3_pkg

## Description
This package builds upon the navvis_description package. Please read documentation for the navvis_description package here:
https://github.com/nathanielmengers/ecse373_f22_nnm22_navvis_description/blob/9c31977cecf064038edf3347cc915be011877369/README.md

By default, this package appends an IMU to the robot described in the navvis_description package. Then, it configures inputs to the navvis_description launch file (display.launch). Additionally, it imports a two dimensional map of Glennan Hall's 5th floor and a bag file representing the robot's LIDAR data and wheel angles as it navigates the building. It also configures a simulated clock such that the Gazebo simulation can be replayed without error. This launch file passes arguments to the navvis_description launch file. With appropriate optional arguments, this package retains functionality of the navvis_description package. 

## Dependencies
- navvis_description
- rosbag
- map_server

## Usage Instructions

To use with default settings, the following command should be executed in command line in the package:
> roslaunch lab3_pkg lab3_launch.launch

### Optional Arguments
- **use_new_xacro** <default = *true*>: If true,
  - Sets the **filename** argument to **append_linkages.xacro**, which adds an IMU to the robot described in the navvis_description package
  - Sets **use_xacro** to *true*
  - Changes the **file** argument so that the file path includes this package instead of navvis_description
  - Sets the **config_file** argument to *config_with_lasers_and_map*. This configuration enable Gazebo to show LIDAR  and map data. Other options include *config.rviz*, *config_with_lasers.rviz*, or a custom configuration file. 
  - To execute the navvis_description launch file with the navvis_description default arguments, set the **use_new_xacro** argument to false:
    > roslaunch lab3_pkg lab3_launch.launch use_new_xacro:=false

  
- **bag_file** <default = *../lab3_pkg/bags/glennan_5_complete.bag*>
  Specifies the source for the bagged data for LIDAR and the robot's position relative to the map. The bag_file argument should include the complete file path, including the directory, name, and extension (.bag) of the file.
  > roslaunch lab3_pkg lab3_launch.launch bag_file:=<file_location/file_name.bag>
  
- See navvis_description documentation for further explanation of optional arguments.
  

