**Turtle2 Follower Node for ROS2 Turtlesim**

This ROS2 package spawns a second turtle (turtle2) in the standard turtlesim simulator and controls it to follow the default turtle1 using a PID controller for smooth tracking.

**Features**

Spawn turtle2 at a specified location with a custom pen color.

Subscribe to pose topics of both turtles.

PID controller to drive turtle2 toward turtle1 smoothly.

Velocity commands are published to /turtle2/cmd_vel.

Stops moving when within a threshold distance of the target.

Uses multi-threaded executor to handle asynchronous operations cleanly.

**Requirements**

ROS2 (tested with Humble)

turtlesim package installed (sudo apt install ros-<ros-distro>-turtlesim)

**Installation**

Clone the repository into your ROS2 workspace:

_cd ~/ros2_ws/src
git clone <your-repo-url>
cd ~/ros2_ws
colcon build
source install/setup.bash_

**Usage**

Launch the turtlesim simulator:

_ros2 run turtlesim turtlesim_node_


Run your follower node:

_ros2 run <your_package_name> <your_executable_name>_


This will:

Spawn turtle2 at (3, 3) with an orange pen.

turtle2 will start following turtle1 using the PID controller.

**Code Structure**

SpawnNode: Handles spawning turtle2 and setting its pen color.

TwistPublisherNode: Subscribes to poses and publishes velocity commands to follow turtle1.

**Parameters (PID gains)**

Linear PID: Kp=1.5, Ki=0.2, Kd=0.05

Angular PID: Kp=8.0, Ki=0.1, Kd=0.1
Can tune these parameters directly in the source code for different behaviors.
