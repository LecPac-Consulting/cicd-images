FROM ghcr.io/lecpac-consulting/cicd-images/base:stable

USER root

ARG KUBECTL_VERSION=v1.35.3
ARG HELM_VERSION=v4.1.4
ARG TERRAFORM_VERSION=1.14.7
ARG OPENTOFU_VERSION=1.11.6
ARG OPENBAO_VERSION=2.5.2

# kubectl
RUN curl -fsSL "https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl" \
      -o /tmp/kubectl && \
    mv /tmp/kubectl /usr/local/bin/kubectl && \
    chmod +x /usr/local/bin/kubectl

# helm
RUN curl -fsSL "https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz" \
      -o /tmp/helm.tar.gz && \
    tar -xzf /tmp/helm.tar.gz -C /tmp && \
    mv /tmp/linux-amd64/helm /usr/local/bin/helm && \
    rm -rf /tmp/helm.tar.gz /tmp/linux-amd64

# terraform
RUN curl -fsSL "https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip" \
      -o /tmp/terraform.zip && \
    unzip /tmp/terraform.zip terraform -d /tmp && \
    mv /tmp/terraform /usr/local/bin/terraform && \
    rm /tmp/terraform.zip

# opentofu
RUN curl -fsSL "https://github.com/opentofu/opentofu/releases/download/v${OPENTOFU_VERSION}/tofu_${OPENTOFU_VERSION}_linux_amd64.zip" \
      -o /tmp/opentofu.zip && \
    unzip /tmp/opentofu.zip tofu -d /tmp && \
    mv /tmp/tofu /usr/local/bin/tofu && \
    rm /tmp/opentofu.zip

# openbao
RUN curl -fsSL "https://github.com/openbao/openbao/releases/download/v${OPENBAO_VERSION}/bao_${OPENBAO_VERSION}_Linux_x86_64.tar.gz" \
      -o /tmp/openbao.tar.gz && \
    tar -xzf /tmp/openbao.tar.gz -C /tmp bao && \
    mv /tmp/bao /usr/local/bin/bao && \
    rm /tmp/openbao.tar.gz

USER 1001
