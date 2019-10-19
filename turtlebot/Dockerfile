# Dockerfile for ROS Kinetic with Gazebo 7 and Turtlebot
# Developed by SCSLab @ Iowa State University

# use ros-kinetic-full image as the base
FROM scslabisu/ros-kinetic-full

# install turtlebot packages
RUN apt-get update && apt-get install -y \
    ros-kinetic-turtlebot \
    ros-kinetic-turtlebot-apps \
    ros-kinetic-turtlebot-interactions \
    ros-kinetic-turtlebot-simulator \
    && apt-get autoremove --purge -y \
    && rm -rf /var/lib/apt/lists/*
