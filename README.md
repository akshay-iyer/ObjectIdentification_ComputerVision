# ObjectIdentification_ComputerVision

Baxter is an industrial robot built by Rethink Robotics. It has two 7 DOF arms, cameras and force sensing actuators attached to it. In this work, we look to explore the utility of Baxter to automate the sorting of fruits into two baskets from a heap. We have used the physics based simulation engine Gazebo for our work. The end-to-end project required the harmony of diverse fields of robotics like dynamic modeling, computer vision, motion planning and robot control. ROS wrappers have been written for all the individual nodes. We have been able to successfully implement the individual nodes and to build a Behavioral master to enable communication between the different nodes. 

This repo consists of the code specific to the Computer Vision track of the project. For the code of the entire project, refer to https://github.com/wpi-dynamics-spring-2019-baxter/BaxterObjectSorting 

The overall system architecture is as follows:
![alt text] (https://github.com/akshay-iyer/ObjectIdentification_ComputerVision/tree/master/images)

The steps involved in classifying fruits is as follows:
1. Dual Threshold HSV segmentation for apples and bananas 

2. Noise removal using morphological operations:

3. Find contours and moments of the fruits to calculate centroids
 
4. Arc length based noise removal to eliminate spurious centroids

5. Fruit identification based on cardinality of pixels in the two contours

6. Passing them as geometry_msgs/PoseStamped ROS message

The steps involved in getting the 3D coordinates from 2D image points:

1. Obtaining a depth pointcloud from kinect through ROS in the Pointcloud Library

2. Extracting type of fruit and the centroid image coordinates from the request 

3. Converting to real world 3D coordinates using PCL and passing as geometry_msgs/PoseStamped ROS message 

4. Frame transformations : Inverted the X and Z axes since kinect and ROS have opposite conventions

5. Provide a translation of 0.35m in X (fwd) and 0.19m in Z (up) to transform the coordinates from the kinect to the base 
