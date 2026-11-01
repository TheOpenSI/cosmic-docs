---
id: getting-started-component-setup
title: Component-Specific Development
sidebar_label: Component-Specific Development
sidebar_position: 4
---

## 7. Component-Specific Development

Use this path when contributing to an individual repository. The detailed commands, supported runtime versions and required environment variables must come from the README in the branch being developed.

### 7.1 `cosmic-core`

- Provides AI orchestration, service routing, model integration, retrieval and response processing.
- Use the Development branch specified for this documentation target.
- Run its tests or launch commands from the branch README after preparing the required services and environment variables.

```bash
git clone -b Development https://github.com/TheOpenSI/cosmic-core.git

cd cosmic-core
```

### 7.2 `cosmic-platform`

- Provides the browser-based front end.
- The repository is structured as a TypeScript application using React and Vite, with API, components, pages, stores and type definitions separated under `src`.
- Use the development branch specified for this documentation target.

```bash
git clone -b development https://github.com/TheOpenSI/cosmic-platform.git

cd cosmic-platform
```

### 7.3 `cosmic-db`

- Provides the FastAPI-based database and endpoint service.
- The repository contains API models, database logic, routers and Alembic migrations for PostgreSQL-backed persistence.
- Use the dev branch specified for this documentation target.

```bash
git clone -b dev https://github.com/TheOpenSI/cosmic-db.git

cd cosmic-db
```

**Database migrations**

For an integrated Docker deployment, use the migration behaviour provided by the current `cosmic-db` container and compose configuration. Do not publish a manual migration command unless it is verified against the target branch.