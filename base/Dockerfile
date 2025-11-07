FROM ubuntu:24.04

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    git \
    jq \
    yq \
    bash \
    curl \
    python3 \
    python3-pip \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
