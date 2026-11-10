---
id: getting-started-overview
title: Getting Started
sidebar_label: Overview
sidebar_position: 1
---

**Documentation status**

This guide targets the active development branches supplied for `cosmic-core`, `cosmic-platform` and `cosmic-db`. Commands and environment-variable names should be checked against the README and example environment files in the same branch before publication.

This guide introduces the supported paths for running the modular CoSMIC platform. It is written for two audiences: users who want to launch the complete platform and contributors who need to work on an individual repository.

**Recommended path**

For a first installation, use the unified `cosmic-docker` repository. It clones and orchestrates `cosmic-core`, `cosmic-platform` and `cosmic-db` together. Use the repository-specific setup only when you need to develop or debug one component.

## 1. Choose Your Setup Path

| Path | Best for | What you run |
|---|---|---|
| Unified Docker | First-time users, demonstrations and integrated testing | `cosmic-core`, `cosmic-platform`, `cosmic-db` and supporting services |
| Repository-specific | Contributors changing one component | One repository plus its required dependencies |
| Native development | Debugging, profiling and local iteration | Services started directly with repository tooling |

## 2. Platform Repositories

- `cosmic-core`, Development branch: https://github.com/TheOpenSI/cosmic-core/tree/Development
- `cosmic-platform`, development branch: https://github.com/TheOpenSI/cosmic-platform/tree/development
- `cosmic-db`, dev branch: https://github.com/TheOpenSI/cosmic-db/tree/dev
- `cosmic-auth`, dev branch: https://github.com/TheOpenSI/cosmic-auth/tree/dev
- `cosmic-docs`, main branch: https://github.com/TheOpenSI/cosmic-docs/tree/main
- Unified Docker packaging: https://github.com/TheOpenSI/cosmic-docker

## 3. Prerequisites

The exact requirements depend on the selected setup. For the unified path, install:

- Git, for cloning the repositories.
- Docker, for building and running the platform services.
- Docker Compose, provided by current Docker Desktop installations or as the Docker Compose plug-in on Linux.
- Sufficient disk space for container images, database storage and any locally hosted language models.
- Network access for the initial clone, image builds and model downloads.

Optional hardware and credentials may be required by the models you select:

- An NVIDIA GPU on Linux when using local GPU acceleration supported by the selected runtime.
- A provider API key when a configured model uses an external model service.
- Hugging Face credentials when a selected repository requires authenticated access.

**Security note**

Do not commit secrets to Git. Create local environment files from the examples provided by each repository and keep credentials outside source control.