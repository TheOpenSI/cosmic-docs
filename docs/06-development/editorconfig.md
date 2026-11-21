---
id: development-editorconfig
title: EditorConfig
sidebar_label: EditorConfig
sidebar_position: 2
---

# EditorConfig conventions

Every CoSMIC repository uses [EditorConfig](https://editorconfig.org) so contributors' editors apply
the same indentation, line endings, character set and whitespace rules. Each repository keeps its
own root `.editorconfig` because not every repository contains the same file types, and each keeps a
matching copy at `docs/conventions/EDITORCONFIG.md`.

## Rules

| Property | Value | Applies to |
| --- | --- | --- |
| `charset` | `utf-8` | all files |
| `end_of_line` | `lf` (`crlf` for `.ps1`, `.bat`, `.cmd`) | all files |
| `insert_final_newline` | `false` | all files |
| `trim_trailing_whitespace` | `true` | all files except Markdown and `.txt` prompts/examples |
| `spelling_language` | `en-AU` | all files |

Indentation is selected per file type and repository:

| Repository | Code | Data, config and Markdown |
| --- | --- | --- |
| `cosmic-auth` | 4 spaces (Python, shell) | 2 spaces |
| `cosmic-core` | 4 spaces (Python, shell) | 2 spaces |
| `cosmic-db` | 4 spaces (Python, shell) | 2 spaces |
| `cosmic-docker` | 2 spaces (all files) | 2 spaces |
| `cosmic-docs` | tabs, width 4 (TypeScript, TSX, JavaScript, JSX, CSS) | 2 spaces |
| `cosmic-platform` | tabs, width 4 (TypeScript, TSX, JavaScript, JSX, CSS) | 2 spaces |

Markdown keeps trailing whitespace because a double space at the end of a line is a hard line break.
`.txt` prompt and example files keep their literal layout, so indentation and trailing whitespace are
not enforced there.

## Editor setup

Install the EditorConfig plugin for your editor (many editors ship it), open the repository root as
the workspace, and the root `.editorconfig` is picked up automatically. Some editors need
EditorConfig enabled in settings.

## Checking your changes

If your editor has an EditorConfig plugin, it applies these rules when you save; that is usually
enough. If it has no plugin, or you want to check from a terminal:

```bash
docker run --rm -v "$PWD:/check" ghcr.io/editorconfig-checker/editorconfig-checker:4.0.2
```

Prebuilt binaries are also on the [editorconfig-checker releases page](https://github.com/editorconfig-checker/editorconfig-checker/releases).

## CI check

Every push and pull request runs [editorconfig-checker](https://github.com/editorconfig-checker/editorconfig-checker)
through each repository's `.github/workflows/editorconfig.yml`. It reads that repository's
`.editorconfig` and `.editorconfig-checker.json`, which lists the paths the checker skips, such as
`LICENSE`, `CONTRIBUTING` and generated or vendored files.

The indentation width (`indent_size`) is applied by your editor; CI checks the indentation style and the regular content rules. Git line endings are also normalised by each repository's `.gitattributes` (`* text=auto eol=lf`).

## References

- [EditorConfig specification](https://spec.editorconfig.org/)
- [Projects using EditorConfig](https://github.com/editorconfig/editorconfig/wiki/Projects-Using-EditorConfig)