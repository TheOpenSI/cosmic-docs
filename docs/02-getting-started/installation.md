---
id: getting-started-installation
title: Quick Installation with Docker
sidebar_label: Installation
sidebar_position: 2
---

The unified Docker repository is the preferred entry point for an integrated deployment. Keep the repositories as sibling directories so the compose build contexts can resolve them consistently.

## 4.1 Create a Workspace and Clone the Repositories

```bash
mkdir cosmic-workspace

cd cosmic-workspace

git clone https://github.com/TheOpenSI/cosmic-db.git
git clone https://github.com/TheOpenSI/cosmic-core.git
git clone https://github.com/TheOpenSI/cosmic-platform.git
git clone https://github.com/TheOpenSI/cosmic-docker.git
```

## 4.2 Select the Documentation Target Branches

For the branch set used by this documentation draft, switch each modular repository explicitly:

```bash
git -C cosmic-core checkout Development
git -C cosmic-platform checkout development
git -C cosmic-db checkout dev
```

**Branch-name caution**

Git branch names are case-sensitive. `cosmic-core` uses "Development" in the supplied URL, while `cosmic-platform` uses "development" and `cosmic-db` uses "dev".

## 4.3 Prepare Local Configuration

Open the README and example environment files in each checked-out branch. Copy the applicable examples to local environment files, then provide deployment-specific values such as database credentials, service addresses, model settings and provider keys.

```bash
# Discover example environment files from the workspace root

find cosmic-core cosmic-platform cosmic-db cosmic-docker -maxdepth 3 \
  -type f \( -name "*.env_example" -o -name ".env.example" -o -name "*.example" \) -print
```

**Why this step is intentionally branch-driven**

Environment-file names and required variables can change as the development branches evolve. The checked-out README and example files are the authoritative setup references for that revision.

## 4.4 Start the Platform

```bash
cd cosmic-docker

docker compose up --build -d
```

The command builds the configured images, starts the services in detached mode and creates the networks and volumes declared by the unified compose definition.

## 4.5 Check Service Health

```bash
docker compose ps

docker compose logs --tail=100
```

Confirm that the expected services are running and inspect logs for configuration, connectivity or migration errors. If a service exits, inspect that service directly:

```bash
docker compose logs <service-name>
```