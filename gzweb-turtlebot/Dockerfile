# Dockerfile for GzWeb with Turtlebot on ROS Kinetic
# Developed by SCSLab @ Iowa State University

# Running instructions:
#   docker run --name gzweb -p 8080:8080 -e "GAZEBO_MASTER_URI=http://172.17.0.2:11345" -d scslabisu/gzweb:turtlebot
# where;
#   --name gzweb => sets container name to "gzweb"
#   -p 8080:8080 => forwards default gzweb port to localhost
#   -e "......." => pass environmental variables to the container
#   -d           => daemonize the container, i.e. run in background

# set the base image
FROM scslabisu/turtlebot

# use nodesource to install node.js v6.x on xenial
RUN curl -sSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - \
    && echo "deb http://deb.nodesource.com/node_6.x xenial main" | tee /etc/apt/sources.list.d/nodesource.list \
    && echo "deb-src http://deb.nodesource.com/node_6.x xenial main" | tee -a /etc/apt/sources.list.d/nodesource.list

# install gzweb dependencies
RUN apt-get update && apt-get install -y \
    libjansson-dev \
    imagemagick \
    nodejs \
    && apt-get autoremove --purge -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*   

# add a non-privilieged user
RUN useradd -ms /bin/bash rosuser

# switch to the non-privilieged user
USER rosuser
WORKDIR /home/rosuser

# get gzweb
RUN hg clone https://bitbucket.org/osrf/gzweb
WORKDIR /home/rosuser/gzweb

# switch to gzweb release branch
RUN hg up default

# copy models to gzweb assets directory
RUN mkdir -p http/client/assets \
    && cp -r /opt/ros/kinetic/share/turtlebot_description http/client/assets \
    && cp -r /opt/ros/kinetic/share/kobuki_description http/client/assets

# process urdf model
#COPY --chown=rosuser:rosuser kobuki_hexagons_asus_xtion_pro.urdf http/client/assets/turtlebot_description/kobuki_hexagons.urdf
#RUN /ros_entrypoint.sh xacro --inorder http/client/assets/turtlebot_description/robots/kobuki_hexagons_kinect.urdf.xacro > http/client/assets/turtlebot_description/kobuki_hexagons.urdf
RUN /ros_entrypoint.sh xacro --inorder http/client/assets/turtlebot_description/robots/kobuki_hexagons_asus_xtion_pro.urdf.xacro > http/client/assets/turtlebot_description/kobuki_hexagons.urdf


# necessary conversion step for gzweb
RUN sed -i 's/package:\/\//model:\/\//g' http/client/assets/turtlebot_description/kobuki_hexagons.urdf

# copy model.config to turtlebot_description
COPY --chown=rosuser:rosuser model.config http/client/assets/turtlebot_description/model.config

# build gzweb
RUN npm install

# use local models
RUN ./deploy.sh -m local

# use gazebo_models
#RUN ./deploy.sh -m

# gzweb uses port 8080 by default
EXPOSE 8080

# launch gzweb
CMD ["npm", "start"]
