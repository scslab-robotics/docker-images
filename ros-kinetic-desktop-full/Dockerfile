# Dockerfile for ROS Kinetic Desktop Full with Gazebo 7
# Developed by SCSLab @ Iowa State University

# based on OSRF ROS Kinetic Desktop Full Dockerfile
# https://github.com/osrf/docker_images/blob/master/ros/kinetic/ubuntu/xenial/desktop-full/Dockerfile

# use ros:kinetic-desktop as the base
FROM osrf/ros:kinetic-desktop-xenial

# install ros packages
RUN apt-get update && apt-get install -y \
    ros-kinetic-desktop-full=1.3.2-0* \
    python-rosinstall-generator \
    rospack-tools \
    && apt-get autoremove --purge -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# expose port number from ROS_MASTER_URI
EXPOSE 11311

# expose port number from GAZEBO_MASTER_URI
EXPOSE 11345
