# Dockerfile for running headless Turtlebot simulations
# Developed by SCSLab @ Iowa State University

# Running instructions
#   docker run --name tbsim -d scslabisu/turtlebot:sim-default
# where;
#   --name tbsim            => sets container name to "tbsim"
#   -d                      => daemonize the container, i.e. run in background
#   -e "3d_sensor=kinect"   => pass "3d_sensor" argument; kinect or asus_xtion_pro
#
# add "-p 11345:11345" to allow connections via gzclient

# use turtlebot image as the base
FROM scslabisu/turtlebot

# add a non-privilieged user
RUN useradd -ms /bin/bash rosuser

# switch to the non-privilieged user
USER rosuser
WORKDIR /home/rosuser

# set turtlebot variables
ARG 3d_sensor=asus_xtion_pro
ENV TURTLEBOT_3D_SENSOR=$3d_sensor

# launch turtlebot simulation
CMD ["roslaunch", "turtlebot_gazebo", "turtlebot_world.launch", "gui:=false"]
