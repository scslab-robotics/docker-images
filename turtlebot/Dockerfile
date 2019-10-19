# Dockerfile for ROS Kinetic, Gazebo 7 and Turtlebot
# Developed by SCSLab @ Iowa State University

# use gazebo7 image as the base
FROM scslabisu/gazebo7

# install requirements
RUN apt-get update && apt-get install -y \
    udev \
	&& apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/*

# install turtlebot packages
RUN apt-get update && apt-get install -y \
    ros-kinetic-turtlebot \
	ros-kinetic-turtlebot-apps \
	ros-kinetic-turtlebot-interactions \
	ros-kinetic-turtlebot-simulator \
	&& apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/*
