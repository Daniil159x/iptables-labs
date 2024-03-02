FROM ubuntu:22.04

RUN --mount=type=cache,target=/var/cache/apt \
    apt update && \
    apt install -y ncat iproute2 procps curl iptables && \
    rm -rf /var/lib/apt/lists
