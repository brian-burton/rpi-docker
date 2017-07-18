# Modified from the original at: https://github.com/node-red/node-red-docker/blob/master/rpi/Dockerfile

FROM brian-burton/rpi-nodejs

LABEL name="Node-Red" build-date="2017-07-17" maintainer="brian-burton@users.noreply.github.com" 

# add support for gpio library, add package.json to install node-red, then sort out non-root user
RUN apt-get update && \
    apt-get install -y wget && \
    mkdir -p /usr/src/node-red && \
    mkdir /data && \
    useradd --home-dir /usr/src/node-red --no-create-home node-red && \
    wget -qO /usr/src/node-red/package.json https://raw.githubusercontent.com/node-red/node-red-docker/master/package.json && \
    chown -R node-red:node-red /data && \
    chown -R node-red:node-red /usr/src/node-red && \
    echo 'deb http://archive.raspberrypi.org/debian/ jessie main ui' > /etc/apt/sources.list.d/raspi.list && \
    wget -qO -  http://archive.raspberrypi.org/debian/raspberrypi.gpg.key | apt-key add - && \
    apt-get update && \
    apt-get install -y python-rpi.gpio && \
    apt-get purge -y --auto-remove wget && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/node-red
USER node-red

RUN npm install

# User configuration directory volume
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json

CMD ["npm", "start", "--", "--userDir", "/data", "--max_old_space_size=256"]
