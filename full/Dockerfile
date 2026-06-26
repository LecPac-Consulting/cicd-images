FROM ghcr.io/lecpac-consulting/cicd-images/base:stable

USER root

ARG KUBECTL_VERSION=v1.35.3
ARG HELM_VERSION=v4.1.4
ARG TERRAFORM_VERSION=1.14.7
ARG OPENTOFU_VERSION=1.11.6
ARG OPENBAO_VERSION=2.5.2
ARG TFLINT_VERSION=0.63.1
ARG TF_SUMMARIZE_VERSION=0.3.20
ARG TF_SUMMARIZE_SHA256=f5c17b24dac6996c79820ee87d53dd7ff86f7df6390b30b6bc0c57ed2873536c
ARG FALCOCTL_VERSION=0.13.0

# Tools
RUN apt-get update && \
    apt-get install --no-install-recommends -y rsync && \
    rm -rf /var/lib/apt/lists/*

# Python
RUN apt-get update && \
    apt-get install --no-install-recommends -y python3 python3-pip python3-venv && \
    rm -rf /var/lib/apt/lists/*

# Install one-time-link CLI
RUN python3 -m venv /opt/one-time-link && \
    /opt/one-time-link/bin/pip install privatebinapi
COPY one-time-link /usr/local/bin/one-time-link
RUN chmod +x /usr/local/bin/one-time-link

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

# tf-summarize
RUN curl -fsSL "https://github.com/dineshba/tf-summarize/releases/download/v${TF_SUMMARIZE_VERSION}/tf-summarize_${TF_SUMMARIZE_VERSION}_linux_amd64.deb" \
      -o /tmp/tf-summarize.deb && \
    echo "${TF_SUMMARIZE_SHA256}  /tmp/tf-summarize.deb" | sha256sum -c - && \
    dpkg -i /tmp/tf-summarize.deb && \
    rm /tmp/tf-summarize.deb

# tflint
RUN curl -fsSL "https://github.com/terraform-linters/tflint/releases/download/v${TFLINT_VERSION}/tflint_linux_amd64.zip" \
      -o /tmp/tflint.zip && \
    unzip /tmp/tflint.zip tflint -d /tmp && \
    mv /tmp/tflint /usr/local/bin/tflint && \
    rm /tmp/tflint.zip

# falcoctl
RUN curl -fsSL "https://github.com/falcosecurity/falcoctl/releases/download/v${FALCOCTL_VERSION}/falcoctl_${FALCOCTL_VERSION}_linux_amd64.tar.gz" \
      -o /tmp/falcoctl.tar.gz && \
    tar -xzf /tmp/falcoctl.tar.gz -C /tmp falcoctl && \
    mv /tmp/falcoctl /usr/local/bin/falcoctl && \
    rm /tmp/falcoctl.tar.gz

USER 1001
