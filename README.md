#Ogmen Path Planning

Explanation of the Chosen Exploration Algorithm:
The chosen exploration algorithm is the Frontier Exploration algorithm. This algorithm is suitable for autonomous exploration tasks as it efficiently navigates the robot to unknown areas in the environment while ensuring complete coverage.
In Frontier Exploration, frontier points are identified as the boundaries between explored and unexplored areas in the map. The robot navigates towards these frontier points to explore unknown regions of the environment. This approach ensures that the robot systematically covers the entire area while avoiding revisiting already explored areas.

Implementation Details of the Exploration Algorithm Node:
Initialization:
The node is initialized with publishers for velocity commands and map data, as well as subscribers for laser scan data.
Map and Laser Scan Callbacks:
The node subscribes to the /map topic to receive map data and /scan topic to receive laser scan data.
The map callback updates the internal map representation and identifies frontier points based on unexplored areas adjacent to explored areas.
The laser scan callback updates the laser scan data used for obstacle avoidance.
Identifying Frontier Points:
The algorithm iterates through the map data to identify frontier points based on the criteria of being adjacent to unexplored areas.
Navigation to Frontier Points:
Once frontier points are identified, the robot navigates towards them using the navigate_to_frontier() method. This method calculates the distance and angle to the nearest frontier point and generates velocity commands to move the robot in that direction.
Exploration Loop:
Within the exploration loop, the node continuously updates the map, identifies frontier points, and navigates towards them to explore the environment.

Instructions for Building and Running the ROS Package:
To build the ROS package containing the astar_node, follow these steps:
Create a ROS workspace if you haven't already.
Clone this package repo into the src directory of your workspace.
Install the required dependencies using rosdep.
Run catkin_make in the root of your workspace to build the package.

To run the ROS node:
Execute this command in a terminal:
roslaunch ogmen_path_planning path_planning.launch


Steps to Visualize the Computed Path in RViz:
In the Rviz window, set the starting position and orientation using "2D Pose Estimate" tool and goal position and orientation using "2D Nav Goal" tool.
The determined path will be shown as a blue line.