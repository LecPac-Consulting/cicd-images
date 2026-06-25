# CI/CD Images

This repository contains images used in various CI/CD pipelines in LecPac Consulting or for its clients.

This provided is maintained by [LecPac Consulting](https://lecpac-consulting.com), a Managed Services Provider (MSP) based in France.
Images are automatically rebuilt every week.

Licensed under the [Apache-2.0](LICENSE) license.

## Available images

- `ghcr.io/lecpac-consulting/cicd-images/base:stable`: The image contains various tools useful in CI/CD pipelines, such as git, jq, yq, bash, curl, python3 and pip.
- `ghcr.io/lecpac-consulting/cicd-images/full:stable`: The image contains all tools from `base` plus additional tools useful in CI/CD pipelines: kubectl, helm, terraform, opentofu, openbao, python (with pip & venv), falcoctl
