# VERSION 1.0.0
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    zeiot/rpi-consul

FROM resin/armv7hf-debian:stretch
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV CONSUL_VERSION 1.0.0

RUN apt-get update \
    && apt-get install -y unzip

ADD https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_arm.zip /consul.zip

RUN addgroup consul \
    && adduser -S -G consul consul

RUN unzip /consul.zip \
    && rm /consul.zip \
    && mv consul /usr/bin/consul \
    && mkdir -p /consul/data \
    && mkdir -p /consul/config \
    && chown -R consul:consul /consul

VOLUME /consul/data
VOLUME /consul/config

# Server RPC is used for communication between Consul clients and servers for internal
# request forwarding.
EXPOSE 8300

# Serf LAN and WAN (WAN is used only by Consul servers) are used for gossip between
# Consul agents. LAN is within the datacenter and WAN is between just the Consul
# servers in all datacenters.
EXPOSE 8301 8301/udp 8302 8302/udp

# HTTP and DNS (both TCP and UDP) are the primary interfaces that applications
# use to interact with Consul.
EXPOSE 8500 8600 8600/udp

ENTRYPOINT [ "/usr/bin/consul" ]

CMD ["agent", "-dev", "-client", "0.0.0.0"]
