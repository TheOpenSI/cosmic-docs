---
id: development
title: Development
sidebar_label: Development
---

## Source Repositories

- `cosmic-core`: https://github.com/TheOpenSI/cosmic-core/tree/Development
- `cosmic-platform`: https://github.com/TheOpenSI/cosmic-platform/tree/development
- `cosmic-db`: https://github.com/TheOpenSI/cosmic-db/tree/dev
- `cosmic-auth`: https://github.com/TheOpenSI/cosmic-auth/tree/dev
- `cosmic-docs`: https://github.com/TheOpenSI/cosmic-docs/tree/main
- `cosmic-docker`: https://github.com/TheOpenSI/cosmic-docker

## Contributing

Confirmed current and unchanged against `CONTRIBUTING.md`:

1. Fork the project.
2. Create a topic branch from `release`.
3. Commit — fix a bug or add a new service.
4. Push to your fork, open a Pull Request.
5. Discuss; maintainers merge or close.
6. Sync `release` back to your fork.

Raise issues on GitHub with a detailed description.

Project layout: `src` (entry point, base classes), `modules` (batch processing, file parsing, service wrappers — one subfolder per topic), `scripts` (config and per-service scripts), `utils` (shared and service-specific tooling). One pull request per new service.