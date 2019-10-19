# Dockerfile for running headless Turtlebot simulations
# Developed by SCSLab @ Iowa State University

# use turtlebot image as the base
FROM scslabisu/turtlebot

# add a non-privilieged user
RUN useradd -ms /bin/bash rosuser

# switch to non-privilieged user
USER rosuser
WORKDIR /home/rosuser

# launch turtlebot simulation
CMD ["roslaunch", "turtlebot_gazebo", "turtlebot_world.launch", "gui:=false"]
