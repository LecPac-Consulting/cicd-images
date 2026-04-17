FROM ubuntu:24.04

RUN groupadd -g 1001 cicd && \
    useradd -m -s /bin/bash -u 1001 -g 1001 cicd 

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    openssh-client \
    git \
    jq \
    yq \
    bash \
    curl \
    unzip \
    python3 \
    python3-pip \
    python3-venv \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl -L -o /usr/local/bin/yq https://github.com/mikefarah/yq/releases/latest/download/yq_linux_amd64 && \
    chmod +x /usr/local/bin/yq

USER 1001
