FROM scratch

LABEL name="Raspbian Jessie Base Image" build-date="2017-07-14" maintainer="brian-burton@users.noreply.github.com" 

ADD raspbian.tar.gz /

RUN apt-get update && \
    apt-get -y upgrade && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
