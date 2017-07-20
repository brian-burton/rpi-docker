FROM brian-burton/raspbian

LABEL name="Consul" build-date="2017-07-20" maintainer="brian-burton@users.noreply.github.com" 

RUN apt-get update && \
    apt-get install -y wget unzip && \
    mkdir -p /consul && \
    useradd --home-dir /consul --no-create-home consul && \
    wget -qO /consul/consul.zip https://releases.hashicorp.com/consul/0.9.0/consul_0.9.0_linux_arm.zip && \
    cd /consul && unzip consul.zip && rm consul.zip && \
    chown -R consul:consul /consul && \
    apt-get purge -y --auto-remove wget unzip && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

USER consul
EXPOSE 8300 8301 8301/udp 8302 8302/udp 8500 8600 8600/udp

CMD ["/consul/consul","agent","-dev","-client","0.0.0.0"]
