# Dockerfile for ROS Kinetic Full with Gazebo 7
# Developed by SCSLab @ Iowa State University

# use ros:kinetic-desktop as the base
FROM osrf/ros:kinetic-desktop-xenial

# install ros packages
RUN apt-get update && apt-get install -y \
    ros-kinetic-desktop-full \
	python-rosinstall-generator \
	wget \
	&& apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/*

# expose port number from ROS_MASTER_URI
EXPOSE 11311

# expose port number from GAZEBO_MASTER_URI
EXPOSE 11345
