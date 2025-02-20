# leo_robot_dlp


**DLP - Drone Landing Platform**

ROS Distribution: Noetic

Robot ROS packages for Leo Rover- custom version with BLDC motors from MAB Robotics.These packages can be run only on the real robot. Not usable for the simulation.

The custom leo_robot_dlp package is based on [leo_robot] package.

* [leo_robot] - Metapackage for this repository.
* [leo_bringup] - Scripts and launch files for starting basic Leo Rover functionalities.
* [leo_fw] - Binary releases of Leo Rover firmware and related utilities.

Visit each package's ROS Wiki page for more information. \
For more information about the robot, visit [Robots/Leo Rover].


## Installation Guide

1. Flash the newest release of [LeoOS].  
   Ensure your rover has the latest operating system installed by following the official LeoOS guide.

2. Connect to the rover via [SSH].  

3. Connect the rover to the [Internet].  
   Ensure the rover is connected to the network for downloading updates and packages.

4. Update packages.  
   Run the following command to update all system packages:  
   ```bash
   sudo apt update
   ```
5. Type the following commands to clone and build the `leo_robot_dlp` package:  
   ```bash
   mkdir -p ~/ros_ws/src
   cd ~/ros_ws/src
   git clone https://github.com/fictionlab/leo_robot_dlp.git
   cd ..
   catkin build
   ```
6. Edit the `setup.bash` file to source from the extended workspace.  
   Open the `/etc/ros/setup.bash` file and ensure it includes the following:  
   ```bash
   # source /opt/ros/noetic/setup.bash
   source /home/pi/ros_ws/devel/setup.bash
   ```
7. Install [CANdle] Python library:
   ```bash
   sudo apt install python3-pip
   python3 -m pip install pyCandleMAB
   ```
8. Enable the [SPI] bus and reboot the system.  
   Open the `/boot/firmware/config.txt` file and uncomment the following line:  
   ```bash
   dtparam=spi=on
   ```
9. Restart leo.service
   ```bash
   sudo systemctl restart leo.service
   ```

[leo_robot]: http://wiki.ros.org/leo_robot
[leo_bringup]: http://wiki.ros.org/leo_bringup
[leo_fw]: http://wiki.ros.org/leo_fw
[LeoOS]: https://docs.fictionlab.pl/leo-rover/guides/software-update
[ssh]: https://docs.fictionlab.pl/leo-rover/guides/ssh
[Internet]: https://docs.fictionlab.pl/leo-rover/guides/connect-to-network
[CANdle]: https://mabrobotics.github.io/MD80-x-CANdle-Documentation/software_package/Candle%20Python%20library.html
[SPI]: https://mabrobotics.github.io/MD80-x-CANdle-Documentation/candle_and_candle_hat/Using%20CANdle.html

