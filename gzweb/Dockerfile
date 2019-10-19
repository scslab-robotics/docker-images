# Dockerfile for GzWeb with Turtlebot
# Developed by SCSLab @ Iowa State University

# set the base image
#FROM scslabisu/turtlebot
FROM scslabisu/ros-kinetic-full

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

# install node.js modules
RUN npm install

# build gzweb
RUN npm run deploy

# gzweb uses port 8080 by default
EXPOSE 8080

# launch gzweb
#CMD ["npm", "start"]
