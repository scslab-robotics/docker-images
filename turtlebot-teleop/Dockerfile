# Dockerfile for running Turtlebot teleop
# Developed by SCSLab @ Iowa State University

# Running instructions
#   docker run --name tbteleop -it scslabisu/turtlebot:teleop
# where;
#   --name tbteleop            => sets the container name
#   -it                        => interactive container
#

# use turtlebot image as the base
FROM scslabisu/turtlebot

# add a non-privilieged user
RUN useradd -ms /bin/bash rosuser

# switch to the non-privilieged user
USER rosuser
WORKDIR /home/rosuser

# launch turtlebot teleop
CMD ["roslaunch", "turtlebot_teleop", "keyboard_teleop.launch"]
