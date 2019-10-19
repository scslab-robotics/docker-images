# Dockerfile for ROS Kinetic and Gazebo 7
# Developed by SCSLab @ Iowa State University

# use ros-kinetic image as the base
FROM scslab/ros-kinetic

# install gazebo packages
RUN sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list' \
	&& wget http://packages.osrfoundation.org/gazebo.key -O - | apt-key add - \
	&& apt-get purge -y wget && apt-get autoremove \
	&& apt-get update && apt-get install -y \
	gazebo7 \
	libgazebo7-dev \
	&& apt-get autoremove --purge -y \
	&& rm -rf /var/lib/apt/lists/*

# expose port number from GAZEBO_MASTER_URI
EXPOSE 11345
