FROM brian-burton/raspbian

LABEL name="Node.js" build-date="2017-07-15" maintainer="brian-burton@users.noreply.github.com" 

RUN apt-get update && \
    apt-get install -y curl && \
    curl https://deb.nodesource.com/setup_6.x -o setupnodejs.sh && \
    chmod u+x setupnodejs.sh && \
    ./setupnodejs.sh && \
    rm setupnodejs.sh && \
    apt-get install -y nodejs && \
    apt-get purge -y --auto-remove curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
